
- *Explanation* : Used to enable [[Bluetooth Stack]] 
- *Parameters* : None
- *Returns* : `esp_err_t` , or `ESP_OK` if successful 
#### Example
____
```c
ret = esp_bluedroid_init() ; 
if(ret){
	ESP_LOGE( GATT_TAG , "%s Failed to initialize bluedroid stack" , __func__ ) ; 
	return ; 
}
```
____ 
Tags : #programming #computer-architecture #graphite