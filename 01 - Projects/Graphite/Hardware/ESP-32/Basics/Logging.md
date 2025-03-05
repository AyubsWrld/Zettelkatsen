#### Include the following dependencies 
---
```c
#include <stdio.h> 
#include "freeRTOS/FreeRTOS.h"
#include "freeRTOS/task.h"
#include "esp_log.h"
```


#### Setup main loop
---
```c 

void app_main(void){
	char *ourTaskName = pcTaskGetName(NULL) ; 
	ESP_LOGI(ourTaskName , "Hello , starting up!") ; 
}
```


____
Tags : #programming #computer-architecture #graphite