- *Explanation* : Function used to register application callbacks with GAP 
- *Parameters* : `esp_gap_cb_t callback`  
- *Returns* : `esp_err_t` , or `ESP_OK` if successful 
#### Example
____
```c
ret = esp_ble_gap_event_handler(gap_event_handler) ; 
if(ret){
	ESP_LOGE( GATT_TAG , "%s Failed to initialize bluedroid stack" , __func__ ) ; 
	return ; 
}
```
____ 
Tags : #programming #computer-architecture #graphite