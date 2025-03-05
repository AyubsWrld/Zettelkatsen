```c
#include "esp_bt.h"
#include "esp_log.h"

void app_main() {
    esp_err_t ret;

    // Initialize the Bluetooth controller
    ret = esp_bt_controller_init();
    if (ret) {
        ESP_LOGE("BT_INIT", "Bluetooth controller init failed: %s", esp_err_to_name(ret));
        return;
    }

    // Enable the Bluetooth controller
    ret = esp_bt_controller_enable(ESP_BT_MODE_CLASSIC_BT);
    if (ret) {
        ESP_LOGE("BT_INIT", "Bluetooth controller enable failed: %s", esp_err_to_name(ret));
        return;
    }

    // Initialize the Bluetooth stack
    ret = esp_bluedroid_init();
    if (ret) {
        ESP_LOGE("BT_INIT", "Bluedroid init failed: %s", esp_err_to_name(ret));
        return;
    }

    // Enable Bluedroid (Bluetooth stack)
    ret = esp_bluedroid_enable();
    if (ret) {
        ESP_LOGE("BT_INIT", "Bluedroid enable failed: %s", esp_err_to_name(ret));
        return;
    }

    ESP_LOGI("BT_INIT", "Bluetooth Classic initialized successfully");
}

```