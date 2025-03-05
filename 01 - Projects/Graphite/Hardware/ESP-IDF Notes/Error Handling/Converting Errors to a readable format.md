Utilizing `esp_err_to_name` function which is defined within the `esp_log.h` header file we can convert `esp_err_t` to readable english . 

#### Example
```c
esp_err_t err = esp_timer_create(&timer_args, &timer_handle);
if(err != ESP_OK){
	ESP_LOGE(Tag , "Error while configurating the timer" , esp_err_to_name(err)) ; 
}
else{
	ESP_LOGI(Tag, "Timer Started Successfully") ; 
}

```
_______
Tags : #programming #computer-architecture #graphite
