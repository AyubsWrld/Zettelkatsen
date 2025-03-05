- *Explanation* : Used to enable bluetooth controller 
- *Parameters* : **Bluetooth Mode** . Takes up one of four values 
	- `ESP_BT_MODE_IDLE` : Bluetooth not running 
	- `ESP_BT_MODE_BLE` : Bluetooth Low Energy Mode
	- `ESP_BT_MODE_CLASSIC_BT` : Bluetooth Classic Mode
	- `ESP_BT_MODE_BTDM` :  Bluetooth Dual Mode ( Classic + BLE ) ; 
- *Returns* : `esp_err_t`  , `ESP_OK` if returns successfully . 

#### Example
____
```c
esp_err_t ret ; 
ret = esp_bt_controller_enable(ESP_BT_MODE_BLE) ; 
if(ret){
	ESP_LOGE(GATT_TAG , "%s Failed to enable bluetooth controller" , __func__ ) ; 
}
```
____ 
Tags : #programming #computer-architecture #graphite