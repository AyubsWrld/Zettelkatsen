```c
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>
#include <string.h>
#include "freertos/FreeRTOS.h"
#include "esp_wifi.h"
#include "esp_timer.h"
#include "esp_event.h"
#include "nvs_flash.h"
#include "lwip/err.h"
#include "lwip/sys.h"
#include "esp_http_server.h"
#include "driver/gpio.h"
#include "cJSON.h"
#include "esp_log.h"
#include "esp_system.h"
#include "esp_netif.h"
#include "esp_mac.h"
#include "sdmmc_cmd.h"
#include "esp_vfs.h"
#include "esp_vfs_fat.h"
#include "driver/sdmmc_host.h"
#include "driver/sdspi_host.h"
#include "driver/spi_common.h"
#include "esp_err.h"
#include "io.h"

#define STA_SSID "TELUS4110"
#define STA_PASS "94wphb3zc5"

#define PARSE_BUFFER 256
#define LED_PIN 2
#define MAX_JSON_SIZE 1024
#define PARSE_TAG "Parsing"
#define WIFI_CONNECTED_BIT BIT0

static const char *TAG = "wifi_ap";
static EventGroupHandle_t wifi_event_group;


typedef struct {
    int    fileSize   ;
    char*  fileName   ;
    int    height     ;
    int    width      ;
    char*  extension  ;
}Image;


char* get_file_name( char* string_to_parse ){
    // Get idx of filenmae
    char* delimeter = "filename=\"" ;
    char* begin = strstr( string_to_parse , delimeter) ;

    int idx = 0 ;
    if(begin){
        begin = begin + strlen(delimeter)  ;
        while(begin[idx] != '\"' && begin[idx] != '\0'){
            idx ++ ;
        }
        char* string_ret_val = malloc(idx + 1) ;
        if(!string_ret_val){
            perror("Failed to allocate memory") ;
            return NULL ;
        }
        strncpy( string_ret_val , begin , idx ) ;
        string_ret_val[idx] = '\0' ;
        return string_ret_val ;
    }else{
        return NULL ;
    }
    return NULL ;
}

int parse_header(char* jpeg_http_request_header, size_t length) {
    unsigned char jpeg_sig[] = { 0xFF, 0xD8, 0xFF, 0xE0 };
    size_t sig_len = sizeof(jpeg_sig);

    for (size_t i = 0; i < length - sig_len; i++) {
        if (memcmp(jpeg_http_request_header + i, jpeg_sig, sig_len) == 0) {
            return (int)(i + sig_len);
        }
    }

    return -1;
}


static void event_handler(void *arg, esp_event_base_t event_base, int32_t event_id, void *event_data)
{
    if (event_base == WIFI_EVENT && event_id == WIFI_EVENT_STA_START)
    {
        esp_wifi_connect();
    }
    else if (event_base == WIFI_EVENT && event_id == WIFI_EVENT_STA_DISCONNECTED)
    {
        ESP_LOGE(TAG, "Wi-Fi Disconnected, retrying...");
        esp_wifi_connect();
    }
    else if (event_base == IP_EVENT && event_id == IP_EVENT_STA_GOT_IP)
    {
        ip_event_got_ip_t *event = (ip_event_got_ip_t *)event_data;
        ESP_LOGI(TAG, "Connected! Assigned IP: " IPSTR, IP2STR(&event->ip_info.ip));
        xEventGroupSetBits(wifi_event_group, WIFI_CONNECTED_BIT);
    }
}

static esp_err_t recv_file(httpd_req_t *req) {
    char content[MAX_JSON_SIZE];
    int recv_size = httpd_req_recv(req, content, MAX_JSON_SIZE - 1);
    if (recv_size <= 0) {
        const char* error_response = "{\"status\":\"error\",\"message\":\"No data received\"}";
        httpd_resp_set_type(req, "application/json");
        httpd_resp_send(req, error_response, strlen(error_response));
        return ESP_OK;
    }

    content[recv_size] = '\0';  // Ensure null termination

    ESP_LOGI(TAG, "Received request: %s", content);

    cJSON *root = cJSON_Parse(content);
    if (root == NULL) {
        const char* error_response = "{\"status\":\"error\",\"message\":\"Invalid JSON\"}";
        httpd_resp_set_type(req, "application/json");
        httpd_resp_send(req, error_response, strlen(error_response));
        return ESP_OK;
    }

    cJSON *filename = cJSON_GetObjectItem(root, "filename");
    if (!filename || !cJSON_IsString(filename) || filename->valuestring == NULL) {
        const char* error_response = "{\"status\":\"error\",\"message\":\"Invalid filename\"}";
        httpd_resp_set_type(req, "application/json");
        httpd_resp_send(req, error_response, strlen(error_response));
        cJSON_Delete(root);
        return ESP_OK;
    }

    char filename_path[64];
    snprintf(filename_path, sizeof(filename_path), "/sdcard/%s", filename->valuestring);

    ESP_LOGI(TAG, "Attempting to open file: %s", filename_path);

    FILE *fptr = fopen(filename_path, "rb");
    if (!fptr) {
        ESP_LOGE(TAG, "Failed to open file: %s (%s)", filename_path, strerror(errno));
        char error_response[128];
        snprintf(error_response, sizeof(error_response),
                 "{\"status\":\"error\",\"message\":\"File not found: %s\"}",
                 filename->valuestring);
        httpd_resp_set_type(req, "application/json");
        httpd_resp_send(req, error_response, strlen(error_response));
        cJSON_Delete(root);
        return ESP_OK;
    }

    // Get file size
    fseek(fptr, 0, SEEK_END);
    long file_size = ftell(fptr);
    fseek(fptr, 0, SEEK_SET);

    ESP_LOGI(TAG, "File size: %ld bytes", file_size);

    // Determine content-type based on file extension
    const char *ext = strrchr(filename->valuestring, '.');
    if (ext) {
        if (strcasecmp(ext, ".jpg") == 0 || strcasecmp(ext, ".jpeg") == 0) {
            httpd_resp_set_type(req, "image/jpeg");
        } else if (strcasecmp(ext, ".png") == 0) {
            httpd_resp_set_type(req, "image/png");
        } else {
            httpd_resp_set_type(req, "application/octet-stream");
        }
    } else {
        httpd_resp_set_type(req, "application/octet-stream");
    }

    // Set Content-Disposition header to suggest filename for download
    char content_disposition[128];
    snprintf(content_disposition, sizeof(content_disposition),
             "attachment; filename=\"%s\"", filename->valuestring);
    httpd_resp_set_hdr(req, "Content-Disposition", content_disposition);

    // Read and send file in chunks
    char *buffer = malloc(1024);
    if (!buffer) {
        ESP_LOGE(TAG, "Failed to allocate memory for buffer");
        fclose(fptr);
        cJSON_Delete(root);
        return ESP_FAIL;
    }

    size_t bytes_read;
    esp_err_t res = ESP_OK;

    while ((bytes_read = fread(buffer, 1, 1024, fptr)) > 0) {
        res = httpd_resp_send_chunk(req, buffer, bytes_read);
        if (res != ESP_OK) {
            ESP_LOGE(TAG, "Error sending file chunk: %s", esp_err_to_name(res));
            break;
        }
    }

    // Send final empty chunk to signal end of response
    if (res == ESP_OK) {
        httpd_resp_send_chunk(req, NULL, 0);
        ESP_LOGI(TAG, "File %s sent successfully", filename->valuestring);
    }

    free(buffer);
    fclose(fptr);
    cJSON_Delete(root);
    return ESP_OK;
}

static void generate_random_filename(char *filename, size_t length) {
    const char charset[] = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
    for (size_t i = 0; i < length; i++) {
        int index = esp_random() % (sizeof(charset) - 1);
        filename[i] = charset[index];
    }
    filename[length] = '\0';
}

static esp_err_t upload_binaries_handler(httpd_req_t *req)
{
    size_t content_length = req->content_len;
    size_t bytes_received = 0;
    char content[1024];
    bool image_started = false;
    char filename[8] = {0};

    generate_random_filename(filename, 7);
    ESP_LOGI(TAG, "Generated random filename: %s", filename);

    FILE *fptr = fopen("/sdcard/test.jpg", "wb");
    if (!fptr) {
        ESP_LOGE(TAG, "Failed to open file");
        return ESP_FAIL;
    }

    while (bytes_received < content_length) {
        int ret = httpd_req_recv(req, content, sizeof(content));
        if (ret <= 0) {
            ESP_LOGE(TAG, "Receive failed");
            fclose(fptr);
            return ESP_FAIL;
        }

        if (!image_started) {
            for (int i = 0; i < ret - 2; i++) {
                if ((unsigned char)content[i] == 0xFF &&
                    (unsigned char)content[i + 1] == 0xD8 && //This only works with jpgs & pngs because { 0xFF , 0xD8 , 0xFF } only 4 jpg images
                    (unsigned char)content[i + 2] == 0xFF) {

                    image_started = true;
                    size_t data_size = ret - i;
                    fwrite(&content[i], 1, data_size, fptr);
                    bytes_received += data_size;
                    break;
                }
            }
        } else {
            fwrite(content, 1, ret, fptr);
            bytes_received += ret;
        }
    }

    fclose(fptr);

    // Create the destination path with the random filename
    char dst_path[64] = "/sdcard/";
    strcat(dst_path, filename);
    strcat(dst_path, ".jpg");

    int error_renaming = rename("/sdcard/test.jpg", dst_path);
    if (error_renaming != 0) {
        ESP_LOGE(TAG, "Error renaming file: %d (%s)", errno, strerror(errno));
    } else {
        ESP_LOGI(TAG, "File successfully renamed to: %s", dst_path);
    }

    // Include the filename in the response
    char resp[64];
    snprintf(resp, sizeof(resp), "{\"status\":\"success\",\"filename\":\"%s.jpg\"}", filename);
    httpd_resp_set_type(req, "application/json");
    httpd_resp_send(req, resp, strlen(resp));

    return ESP_OK;
}

static esp_err_t upload_file_handler(httpd_req_t *req)
{
    char content[MAX_JSON_SIZE];
    int ret = httpd_req_recv(req, content, sizeof(content));

    if (ret <= 0) {
        const char* error_response = "{\"status\":\"error\",\"message\":\"No data received\"}";
        httpd_resp_set_type(req, "application/json");
        httpd_resp_send(req, error_response, strlen(error_response));
        return ESP_OK;
    }

    content[ret] = '\0';

    cJSON *root = cJSON_Parse(content);
    if (root == NULL) {
        const char* error_response = "{\"status\":\"error\",\"message\":\"Invalid JSON\"}";
        httpd_resp_set_type(req, "application/json");
        httpd_resp_send(req, error_response, strlen(error_response));
        return ESP_OK;
    }

    struct {
        const char *key;
        cJSON_bool (*validate)(const cJSON *item);
    } fields[] = {
        {"fileName", cJSON_IsString},
        {"fileSize", cJSON_IsNumber},
        {"height",   cJSON_IsNumber},
        {"width",    cJSON_IsNumber},
        {"extension", cJSON_IsString}
    };

    for (size_t i = 0; i < sizeof(fields) / sizeof(fields[0]); i++) {
        cJSON *item = cJSON_GetObjectItem(root, fields[i].key);
        if (!item || !fields[i].validate(item)) {
            ESP_LOGE(TAG, "Invalid or missing '%s'", fields[i].key);
            char error_response[128];
            snprintf(error_response, sizeof(error_response),
                     "{\"status\":\"error\",\"message\":\"Invalid or missing '%s'\"}", fields[i].key);
            httpd_resp_send(req, error_response, strlen(error_response));
            cJSON_Delete(root);
            return ESP_OK;
        }
    }

    ESP_LOGI(TAG, "Received: fileName=%s, fileSize=%d, height=%d, width=%d, extension=%s",
             cJSON_GetObjectItem(root, "fileName")->valuestring,
             cJSON_GetObjectItem(root, "fileSize")->valueint,
             cJSON_GetObjectItem(root, "height")->valueint,
             cJSON_GetObjectItem(root, "width")->valueint,
             cJSON_GetObjectItem(root, "extension")->valuestring);

    cJSON_Delete(root);

    const char* success_response = "{\"status\":\"success\",\"message\":\"Data received\"}";
    httpd_resp_set_type(req, "application/json");
    httpd_resp_send(req, success_response, strlen(success_response));

    return ESP_OK;
}

static esp_err_t get_json_handler(httpd_req_t *req)
{
    cJSON *root = cJSON_CreateObject();

    cJSON_AddStringToObject(root, "name", "Test JSON");
    cJSON_AddNumberToObject(root, "uptime", esp_timer_get_time() / 1000000);
    cJSON_AddBoolToObject(root, "led_state", gpio_get_level(LED_PIN));
    char *json_string = cJSON_Print(root);
    httpd_resp_set_type(req, "application/json");
    httpd_resp_send(req, json_string, strlen(json_string));

    free(json_string);
    cJSON_Delete(root);

    return ESP_OK;
}


static esp_err_t root_handler(httpd_req_t *req)
{
    cJSON *root = cJSON_CreateObject();

    cJSON_AddStringToObject(root, "name", "Test JSON");
    cJSON_AddNumberToObject(root, "uptime", esp_timer_get_time() / 1000000);
    cJSON_AddBoolToObject(root, "led_state", gpio_get_level(LED_PIN));
    char *json_string = cJSON_Print(root);
    httpd_resp_set_type(req, "application/json");
    httpd_resp_send(req, json_string, strlen(json_string));

    free(json_string);
    cJSON_Delete(root);

    return ESP_OK;
}

httpd_uri_t uri_root = {
    .uri = "/",
    .method = HTTP_GET,
    .handler = root_handler,
    .user_ctx = NULL
};

httpd_uri_t uri_get_json = {
    .uri = "/api/json",
    .method = HTTP_GET,
    .handler = get_json_handler,
    .user_ctx = NULL
};

httpd_uri_t uri_upload_file = {
    .uri = "/upload" ,
    .method = HTTP_POST,
    .handler = upload_file_handler,
    .user_ctx = NULL
};

httpd_uri_t uri_get_file = {
    .uri = "/recv" ,
    .method = HTTP_POST,
    .handler = recv_file,
    .user_ctx = NULL
};

httpd_uri_t uri_upload_binaries = {
    .uri = "/binaries" ,
    .method = HTTP_POST,
    .handler = upload_binaries_handler,
    .user_ctx = NULL
};


static httpd_handle_t start_webserver(void)
{
    httpd_handle_t server = NULL;
    httpd_config_t config = HTTPD_DEFAULT_CONFIG();
    config.max_uri_handlers = 5;

    if (httpd_start(&server, &config) == ESP_OK) {
        httpd_register_uri_handler(server, &uri_root);
        httpd_register_uri_handler(server, &uri_upload_file);
        httpd_register_uri_handler(server, &uri_get_json);
        httpd_register_uri_handler(server, &uri_get_file);
        httpd_register_uri_handler(server, &uri_upload_binaries);
        ESP_LOGI(TAG, "Server started on port: '%d'", config.server_port);
        return server;
    }

    ESP_LOGI(TAG, "Error starting server!");
    return NULL;
}

static void wifi_init_sta()
{
    wifi_event_group = xEventGroupCreate();
    ESP_ERROR_CHECK(esp_netif_init());
    ESP_ERROR_CHECK(esp_event_loop_create_default());

    esp_netif_t *netif = esp_netif_create_default_wifi_sta();
    ESP_ERROR_CHECK(esp_netif_dhcpc_start(netif));

    wifi_init_config_t cfg = WIFI_INIT_CONFIG_DEFAULT();
    ESP_ERROR_CHECK(esp_wifi_init(&cfg));

    ESP_ERROR_CHECK(esp_event_handler_instance_register(WIFI_EVENT, ESP_EVENT_ANY_ID, &event_handler, NULL, NULL));
    ESP_ERROR_CHECK(esp_event_handler_instance_register(IP_EVENT, IP_EVENT_STA_GOT_IP, &event_handler, NULL, NULL));

    wifi_config_t wifi_sta_config = {
        .sta = {
            .ssid = STA_SSID,
            .password = STA_PASS,
            .threshold.authmode = WIFI_AUTH_WPA2_PSK,
        },
    };

    ESP_ERROR_CHECK(esp_wifi_set_mode(WIFI_MODE_STA));
    ESP_ERROR_CHECK(esp_wifi_set_config(WIFI_IF_STA, &wifi_sta_config));
    ESP_ERROR_CHECK(esp_wifi_start());

    ESP_LOGI(TAG, "Wi-Fi STA Mode Started, waiting for IP...");
    xEventGroupWaitBits(wifi_event_group, WIFI_CONNECTED_BIT, pdFALSE, pdTRUE, portMAX_DELAY);
}

void app_main(void)
{
    esp_err_t ret = nvs_flash_init();
    if (ret == ESP_ERR_NVS_NO_FREE_PAGES || ret == ESP_ERR_NVS_NEW_VERSION_FOUND) {
        ESP_ERROR_CHECK(nvs_flash_erase());
        ret = nvs_flash_init();
    }
    ESP_ERROR_CHECK(ret);

    gpio_reset_pin(LED_PIN);
    gpio_set_direction(LED_PIN, GPIO_MODE_OUTPUT);

    wifi_init_sta();

    esp_log_level_set("*", ESP_LOG_INFO);
    init_sd_card();

    start_webserver();
}
```