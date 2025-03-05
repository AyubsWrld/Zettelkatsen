```c
#include <stdio.h>
#include <string.h>
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"
#include "esp_log.h"         // ESP-IDF logging system
#include "esp_wifi.h"        // Wi-Fi functions
#include "esp_event.h"       // Event loop library
#include "nvs_flash.h"       // Non-volatile storage

#define WIFI_SSID "Guest"      // SSID of the network
#define WIFI_PASS "12345678"      // Password (minimum 8 characters)
#define WIFI_CHANNEL 1            // Wi-Fi channel (1-13)
#define MAX_STA_CONN 4            // Max number of devices that can connect

static const char *TAG = "WiFi_AP"; // Tag for logging

void wifi_init_softap(void)
{
    // Initialize the Wi-Fi driver
    wifi_init_config_t cfg = WIFI_INIT_CONFIG_DEFAULT();
    ESP_ERROR_CHECK(esp_wifi_init(&cfg));

    // Configure Wi-Fi settings for AP mode
    wifi_config_t wifi_config = {
        .ap = {
            .ssid = WIFI_SSID,
            .ssid_len = strlen(WIFI_SSID),
            .channel = WIFI_CHANNEL,
            .password = WIFI_PASS,
            .max_connection = MAX_STA_CONN,
            .authmode = WIFI_AUTH_WPA_WPA2_PSK,
        },
    };

    if (strlen(WIFI_PASS) == 0) {
        wifi_config.ap.authmode = WIFI_AUTH_OPEN; // Open network if no password
    }

    // Start the Wi-Fi in AP mode
    ESP_ERROR_CHECK(esp_wifi_set_mode(WIFI_MODE_AP));
    ESP_ERROR_CHECK(esp_wifi_set_config(WIFI_IF_AP, &wifi_config));
    ESP_ERROR_CHECK(esp_wifi_start());

    ESP_LOGI(TAG, "Wi-Fi access point started with SSID: %s, Password: %s", WIFI_SSID, WIFI_PASS);
}

void app_main(void)
{
    // Initialize NVS (required for Wi-Fi)
    esp_err_t ret = nvs_flash_init();
    if (ret == ESP_ERR_NVS_NO_FREE_PAGES || ret == ESP_ERR_NVS_NEW_VERSION_FOUND) {
        ESP_ERROR_CHECK(nvs_flash_erase());
        ret = nvs_flash_init();
    }
    ESP_ERROR_CHECK(ret);

    // Initialize event loop
    ESP_ERROR_CHECK(esp_event_loop_create_default());

    // Initialize Wi-Fi in AP mode
    wifi_init_softap();

    // Keep the program running
    while (1) {
        vTaskDelay(pdMS_TO_TICKS(1000));
    }
}

```

____
Tags : #programming #computer-architecture #graphite