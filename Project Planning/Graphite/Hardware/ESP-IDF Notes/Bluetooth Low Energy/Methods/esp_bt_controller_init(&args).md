- *Explanation* : Used to initialize the Bluetooth Controller to allocate tasks and resources . 
- *Parameters* : Configuration structure of type `esp_bt_config_t` 
- *Returns* : `esp_err_t`  , `ESP_OK` if returns successfully . 

#### Example
____
```c
esp_err_t ret ; 
ret = esp_bt_controller_init(&bt_cfg) ; 
if(ret){
	ESP_LOGE(GATT_TAG , "%s Failed to initialize bluetooth controller" , __func__ ) ; 
}
```
____ 
Tags : #programming #computer-architecture #graphite