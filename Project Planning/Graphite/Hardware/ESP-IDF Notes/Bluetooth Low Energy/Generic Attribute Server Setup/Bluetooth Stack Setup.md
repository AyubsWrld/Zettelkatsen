> [!tldr] 
> The process to get the server goes as follows .. 
> *Setup Non-Volatile Flash Memory* 
> *Setup Bluetooth Stack By first initializing then enabling*
> *Setup Bluedroid By first initializing then enabling*
> *Setup callback functions for both GATT and GAP*
> *Setup Profiles*

## Flow 
___
## **Non-Volatile Memory Instantiation**
___
The entry point of the application serves to carry out three main jobs . Firstly , the app instantiates **Non-Volatile Storage ( *Flash Memory* )** Utilizing [[nvs_flash.h]] . 

> [!note] **Error Handling Convention** 
> Throughout our server, we utilize an instance of `esp_err_t ret`  to store any potential errors which may return from the process of instantiating the Bluetooth server . For example , 
> ```c 
> esp_err_t ret ; 
> ret = nvs_flash_init() ;  // Attempt to instantiate the Non-Volatile Storage
> if(ret == ESP_ERR_NVS_NO_FREE_PAGES | ret == ESP_ERR_NVS_NEW_VERSION_FOUND){
> 	ESP_ERROR_CHECK(nvs_flash_erase) ; 
> 	ret = nvs_flash_init()
> }
> ESP_ERROR_CHECK( ret ) ; 
> ```
>Through doing so , we can simply check whether an error has Occured anywhere within the code and log accordingly utilizing `ESP_LOGE()` 
	
## **Bluetooth Controller Setup**
___
#### Bluetooth controller configuration  
___
Our next step involves Initializing a [[Bluetooth Controller]] with default settings . This is done through the use of a predefined [[Configuration Structure]] which has the default settings 

```c
esp_bt_controller_config_t bt_cfg = BT_CONTROLLER_INIT_CONFIG_DEFAULT() ; // default cfg
ret = esp_bt_controller_init(&bt_cfg) ; // Struct which contains all the args
```

As per convention , `ret` is then used in potential error logging and premature returning ensues .. 

```c
if(ret){
	ESP_LOGE(GATTS_TAG, "%s initialize controller failed" __func__)  ; 
	return  ;
}
```

#### Bluetooth controller enabling 
___
After we have successfully configured our [[Bluetooth Controller]] , We can then focus on actually enabling the Bluetooth Controller 

```c
ret = esp_bt_controller_enable(ESP_BT_MODE_BLE) 
if(ret){
	ESP_LOGE(GATT_TAG , "%s Error Occured while enabling bluetooth controller" , __func__ ) ; 
	return ; 
}
```

## **Bluedroid Setup**
____
Next we concern ourselves with the setup of the [[Bluedroid Stack]]  , which includes the common definitions and APIs for both BT classic and BLE , It is initialized and enabled by using these two functions .. 
#### Bluedroid Initialization 
___
Firstly we enable the Bluedroid stack through the use of [[esp_bluedroid_init()]] . 

```c
ret = esp_bluedroid_init() ; 
if(ret){ 
	ESP_LOGE(GATT_TAG , "%s Error occured while initializing bluedroid stack" , __func__) ; 
	return ; 
}
```
#### Bluedroid Enabling 
___
Next we enable the Bluedroid stack using [[esp_bluedroid_enable()]] 

```c 
ret = esp_bluedroid_enable(); 
if(ret){
	ESP_LOGE(GATT_TAG , "%s Error Occured while enabling Bluedroid Stack" , __func__);
	return ; 
}
```

## **Profile Setup**
____
Now at this point , the Bluetooth stack is setup , however we are missing the core functionality of allowing the application to respond to read/write operations as well as connections . For this we must set up Callback Functions . The two main managers of events are the [[GAP and GATT event handlers]]  . The application needs to register a callback function for each event handler in order to let the application know which functions are going to handle the GAP and GATT events . 

### GATT Event Handler 
___
Utilizing the function `esp_ble_gatts_register_callback` 
```c
ret = esp_ble_register_callback(gatts_event_handler) ;
if(ret){
 ESP_LOGE(GATT_TAG , "%s Failed to GATT initialize callback function",__func__) ; 
}
```
### GAP Event Handler 
___
Utilizing the function `esp_ble_gap_register_callback(gap_event_handler)`
```c
ret = esp_ble_gap_register_callback(gap_event_handler) ;
if(ret){
	ESP_LOGE( GATT_TAG , "%s Failed to initialize GAP callback function" , __func__ ) ; 
	return ; 
}
```
____
Tags : #programming #computer-architecture #graphite