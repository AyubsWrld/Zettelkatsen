## Flow 
___
#### Non-Volatile Memory Instantiation 
___
The entry point of the application serves to carry out three main jobs . Firstly , the app instantiates **Non-Volatile Storage ( *Flash Memory* )** Utilizing [[nvs_flash.h]] . 

> [!note] **Error Handling Convention** 
> Throughout our server, we utilize an instance of `esp_err_t ret`  to store any potential errors which may return from the process of instantiating the Bluetooth server . For example , 
> ```c 
> esp_err_t ret ; 
> ret = nvs_flash_init() ;  // Attempt to instantiate the Non-Volatile Storage
> if(ret == ESP_ERR_NVS_NO_FREE_PAGES | ret == ESP_ERR_NVS_NEW_VERSION_FOUND){
> 	ESP_ERROR_CHECK(nvs_flash_erase) ; 
> 	ret = nvs_flash_inti()
> }
> ESP_ERROR_CHECK( ret ) ; 
> ```
>Through doing so , we can simply check whether an error has Occured anywhere within the code and log accordingly utilizing `ESP_LOGE()` 

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







____
Tags : #programming #computer-architecture #graphite