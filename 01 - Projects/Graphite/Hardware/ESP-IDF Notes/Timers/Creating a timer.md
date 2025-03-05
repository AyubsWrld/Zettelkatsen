### Includes 
___
```c
#include <stdio.h>
#include "esp_timer.h"
#include "esp_log.h"
```

#### Globals
____

```c
#define TAG "TIMER_LOG"  // Tag used for logging
```

#### Callback
_____
```c
// Timer callback function
void log_message_callback(void* arg) {
    static int counter = 0;  // Counter to keep track of callback executions
    ESP_LOGI(TAG, "Timer triggered! Counter value: %d", ++counter);
}
```

#### Main
___
```c
void app_main(void) {
    // Timer configuration structure
    const esp_timer_create_args_t timer_args = {
        .callback = &log_message_callback,  // Callback function
        .arg = NULL,                        // No additional argument
        .name = "Logging Timer"             // Timer name
    };

    esp_timer_handle_t timer_handle;

    // Create the timer
    esp_err_t err = esp_timer_create(&timer_args, &timer_handle);
    if (err != ESP_OK) {
        ESP_LOGE(TAG, "Failed to create timer: %s", esp_err_to_name(err));
        return;
    }

    // Start the timer to trigger every 2 seconds (2000000 microseconds)
    err = esp_timer_start_periodic(timer_handle, 2000000);
    if (err != ESP_OK) {
        ESP_LOGE(TAG, "Failed to start timer: %s", esp_err_to_name(err));
        return;
    }

    ESP_LOGI(TAG, "Timer started successfully!");
}

```

____
Tags : #programming #computer-architecture #graphite