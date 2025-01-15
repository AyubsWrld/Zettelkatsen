```c
#include <string.h>
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"
#include "esp_wifi.h"
#include "esp_system.h"
#include "esp_event.h"
#include "esp_log.h"
#include "nvs_flash.h"
#include "lwip/err.h"
#include "lwip/sys.h"
#include "esp_http_server.h"
#include "driver/gpio.h"  // Added for GPIO control

#define AP_SSID "MyESP32"
#define TAG "WIFI_SERVER"
#define AP_PASS "12345678"
#define LED_PIN 2  // Built-in LED pin number

static const char *TAG = "wifi_ap"; // What is this for ? 

// Data to be sent to the client 
const char* html_page = "<!DOCTYPE html><html>\
<head><title>ESP32 Control</title></head>\
<body>\
    <h1>ESP32 Web Server</h1>\
    <p>Temperature: <span id='temp'>--</span>°C</p>\
    <button onclick='getData()'>Get Data</button>\
    <button onclick='toggleLED()'>Toggle LED</button>\
    <script>\
        function getData() {\
            fetch('/data')\
                .then(response => response.text())\
                .then(data => {\
                    document.getElementById('temp').innerText = data;\
                });\
        }\
        function toggleLED() {\
            fetch('/toggle');\
        }\
    </script>\
</body></html>";

// Function to handle root URL
static esp_err_t root_handler(httpd_req_t *req)
{
    httpd_resp_send(req, html_page, strlen(html_page));
    return ESP_OK;
}

// Function to handle data request
static esp_err_t data_handler(httpd_req_t *req)
{
    // Example: sending a simulated temperature value
    char resp[32];
    sprintf(resp, "23.5");
    httpd_resp_send(req, resp, strlen(resp));
    return ESP_OK;
}

// Function to handle LED toggle
static esp_err_t toggle_handler(httpd_req_t *req)
{
    static bool led_state = false;
    led_state = !led_state;
    gpio_set_level(LED_PIN, led_state);
    httpd_resp_send(req, "OK", 2);
    return ESP_OK;
}

// HTTP server configuration
httpd_uri_t uri_root = {
    .uri = "/",
    .method = HTTP_GET,
    .handler = root_handler,
    .user_ctx = NULL
};

httpd_uri_t uri_data = {
    .uri = "/data",
    .method = HTTP_GET,
    .handler = data_handler,
    .user_ctx = NULL
};

httpd_uri_t uri_toggle = {
    .uri = "/toggle",
    .method = HTTP_GET,
    .handler = toggle_handler,
    .user_ctx = NULL
};

// Start the HTTP server
static httpd_handle_t start_webserver(void)
{
    httpd_handle_t server = NULL;
    httpd_config_t config = HTTPD_DEFAULT_CONFIG();

    if (httpd_start(&server, &config) == ESP_OK) {
        httpd_register_uri_handler(server, &uri_root);
        httpd_register_uri_handler(server, &uri_data);
        httpd_register_uri_handler(server, &uri_toggle);
        // printf("Server started on port: '%d'\n", config.server_port);
        ESP_LOGI(TAG , "Server has begun %d/n" , config.server_port);
        return server;
    }

    printf("Error starting server!\n");
    return NULL;
}

static void wifi_init_ap(void)
{
    ESP_ERROR_CHECK(esp_netif_init());
    ESP_ERROR_CHECK(esp_event_loop_create_default());
    esp_netif_create_default_wifi_ap();

    wifi_init_config_t cfg = WIFI_INIT_CONFIG_DEFAULT();
    ESP_ERROR_CHECK(esp_wifi_init(&cfg));

    wifi_config_t wifi_ap_config = {
        .ap = {
            .ssid = AP_SSID,
            .ssid_len = strlen(AP_SSID),
            .password = AP_PASS,
            .max_connection = 4,
            .authmode = WIFI_AUTH_WPA_WPA2_PSK
        },
    };

    ESP_ERROR_CHECK(esp_wifi_set_mode(WIFI_MODE_AP));
    ESP_ERROR_CHECK(esp_wifi_set_config(WIFI_IF_AP, &wifi_ap_config));
    ESP_ERROR_CHECK(esp_wifi_start());

    printf("WiFi AP Started\n");
    printf("SSID: %s\n", AP_SSID);
    printf("Password: %s\n", AP_PASS);
}

void app_main(void)
{
    // Initialize NVS
    esp_err_t ret = nvs_flash_init();
    if (ret == ESP_ERR_NVS_NO_FREE_PAGES || ret == ESP_ERR_NVS_NEW_VERSION_FOUND) {
        ESP_ERROR_CHECK(nvs_flash_erase());
        ret = nvs_flash_init();
    }
    ESP_ERROR_CHECK(ret);

    // Configure LED pin
    gpio_reset_pin(LED_PIN);
    gpio_set_direction(LED_PIN, GPIO_MODE_OUTPUT);

    // Start WiFi AP
    wifi_init_ap();

    // Start HTTP server
    start_webserver();
}

```
____
Tags : #programming #computer-architecture #graphite