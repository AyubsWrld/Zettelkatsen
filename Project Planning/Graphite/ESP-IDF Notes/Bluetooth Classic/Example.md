#### Includes
___
```c
#include <stdio.h>
#include "nvs_flash.h"
#include "esp_bt.h"
#include "esp_bt_main.h"
#include "esp_bt_device.h"
#include "esp_spp_api.h"
```

> [!info] stdio.h
> Header for standard input output operations 

> [!info]  nvs_flash.h 
>  Header for Non-volatile ( Persistent ) storage . It is used to access the non-volatile storage functionalities of the ESP32. Allowing it to retain data after power is disconnected . It is used to enable the Bluetooth stack initialization to access persistent storage which is used to store pairing information , such as bonded devices and keys  . it's use can be observed within this code snippet ... 
>  ```c
>  esp_err_t ret = nvs_flash_init();
>  if (ret == ESP_ERR_NVS_NO_FREE_PAGES || ret == ESP_ERR_NVS_NEW_VERSION_FOUND){
> 	 ESP_ERROR_CHECK(nvs_flash_erase());
> 	 ret = nvs_flash_init(); 
>  }
>  ESP_ERROR_CHECK(ret);
>  ```



#### callback
___
```c
#define DEVICE_NAME "ESP32_BT_SERVER"
```
```c
static void esp_spp_callback(esp_spp_cb_event_t event, esp_spp_cb_param_t *param) {
    switch (event) {
        case ESP_SPP_INIT_EVT:
            printf("SPP Initialized\n");
            esp_spp_start_srv(ESP_SPP_SEC_NONE, ESP_SPP_ROLE_SLAVE, 0, DEVICE_NAME);
            break;
        case ESP_SPP_DATA_IND_EVT:
            printf("Data received: %.*s\n", param->data_ind.len, param->data_ind.data);
            break;
        case ESP_SPP_OPEN_EVT:
            printf("Client connected\n");
            break;
        case ESP_SPP_CLOSE_EVT:
            printf("Client disconnected\n");
            break;
        default:
            break;
    }
}```

#### Application Entry Point
____
```c

void app_main(void) {
    // Initialize NVS
    esp_err_t ret = nvs_flash_init();
    if (ret == ESP_ERR_NVS_NO_FREE_PAGES || ret == ESP_ERR_NVS_NEW_VERSION_FOUND) {
        ESP_ERROR_CHECK(nvs_flash_erase());
        ret = nvs_flash_init();
    }
    ESP_ERROR_CHECK(ret);

    // Initialize Bluetooth controller
    esp_bt_controller_config_t bt_cfg = BT_CONTROLLER_INIT_CONFIG_DEFAULT();
    ESP_ERROR_CHECK(esp_bt_controller_init(&bt_cfg));
    ESP_ERROR_CHECK(esp_bt_controller_enable(ESP_BT_MODE_CLASSIC_BT));

    // Initialize Bluedroid
    ESP_ERROR_CHECK(esp_bluedroid_init());
    ESP_ERROR_CHECK(esp_bluedroid_enable());

    // Register the SPP callback
    ESP_ERROR_CHECK(esp_spp_register_callback(esp_spp_callback));
    ESP_ERROR_CHECK(esp_spp_init(ESP_SPP_MODE_CB));

    // Set the device name
    ESP_ERROR_CHECK(esp_bt_dev_set_device_name(DEVICE_NAME));

    // Make the device discoverable and connectable
    ESP_ERROR_CHECK(esp_bt_gap_set_scan_mode(ESP_BT_SCAN_MODE_CONNECTABLE_DISCOVERABLE));

    printf("Bluetooth Classic SPP server started. Device name: %s\n", DEVICE_NAME);
}

```
____
Tags : #programming #computer-architecture #graphite