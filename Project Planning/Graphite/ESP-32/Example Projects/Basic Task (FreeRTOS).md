```c
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"
#include "esp_log.h"

void task_function(void *pvParameter)
{
    while (1)
    {
        ESP_LOGI("Task", "Running in the background");
        vTaskDelay(1000 / portTICK_PERIOD_MS);  // Task delay
    }
}

void app_main(void)
{
    xTaskCreate(task_function, "Background Task", 2048, NULL, 1, NULL);
}

```


____
Tags : #programming #computer-architecture #graphite