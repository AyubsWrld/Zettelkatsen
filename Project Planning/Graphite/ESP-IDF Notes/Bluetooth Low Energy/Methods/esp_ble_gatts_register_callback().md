- *Explanation* : This function is called to register application callbacks with BTA GATTS module.
- *Parameters* : `esp_gatts_cb_t callback`
- *Returns* : `esp_err_t` , or `ESP_OK` if successful 
#### Example
____
```c
ret = esp_ble_gatts_register_callback(gatts_event_handler) ; 
if(ret){
	ESP_LOGE( GATT_TAG , "%s Failed to initialize bluedroid stack" , __func__ ) ; 
	return ; 
}
```
____ 
Tags : #programming #computer-architecture #graphite