### 2. **Basic Task (FreeRTOS)**:

Create a simple task that runs independently and logs messages.

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

**Key Concepts:**

- FreeRTOS task creation (`xTaskCreate`)
- Task delay (`vTaskDelay`)

---

### 3. **Button Press with Interrupt**:

Use GPIO interrupts to detect a button press (e.g., turning an LED on/off with a button).

```c
#include "driver/gpio.h"
#include "esp_log.h"

#define LED_PIN GPIO_NUM_2
#define BUTTON_PIN GPIO_NUM_0

static void IRAM_ATTR button_isr_handler(void* arg)
{
    static bool led_state = false;
    led_state = !led_state;
    gpio_set_level(LED_PIN, led_state);
}

void app_main(void)
{
    // Initialize LED as output
    gpio_set_direction(LED_PIN, GPIO_MODE_OUTPUT);
    // Initialize button as input with pull-up
    gpio_set_direction(BUTTON_PIN, GPIO_MODE_INPUT);
    gpio_pullup_en(BUTTON_PIN);

    // Install ISR service
    gpio_set_intr_type(BUTTON_PIN, GPIO_INTR_POSEDGE);  // Trigger on button press
    gpio_isr_handler_add(BUTTON_PIN, button_isr_handler, NULL);
    gpio_intr_enable(BUTTON_PIN);

    ESP_LOGI("Main", "Press button to toggle LED");
}
```

**Key Concepts:**

- Interrupt service routines (ISR)
- Configuring interrupts (`gpio_set_intr_type`)
- GPIO pin with pull-up/down resistors (`gpio_pullup_en`)
- GPIO ISR handling (`gpio_isr_handler_add`)

---

### 4. **Delay Without Using FreeRTOS**:

Sometimes, you just need a simple delay. Here’s how you can do it without using FreeRTOS functions.

```c
#include "driver/gpio.h"
#include "esp_system.h"

#define LED_PIN GPIO_NUM_2

void app_main(void)
{
    gpio_set_direction(LED_PIN, GPIO_MODE_OUTPUT);
    while (1)
    {
        gpio_set_level(LED_PIN, 1);  // LED on
        ets_delay_us(1000000);  // Delay for 1 second (1,000,000 microseconds)
        gpio_set_level(LED_PIN, 0);  // LED off
        ets_delay_us(1000000);  // Delay for 1 second
    }
}
```

**Key Concepts:**

- `ets_delay_us`: A non-blocking delay function in microseconds.
- Simple GPIO control.

---

### 5. **Reading Analog Input (ADC)**:

Reading an analog sensor like a potentiometer using the ADC (Analog to Digital Converter) on the ESP32.

```c
#include "driver/adc.h"
#include "esp_log.h"

#define ADC_CHANNEL ADC1_CHANNEL_0  // GPIO36 (default)

void app_main(void)
{
    adc1_config_width(ADC_WIDTH_BIT_12);    // 12-bit ADC resolution (0-4095)
    adc1_config_channel_atten(ADC_CHANNEL, ADC_ATTEN_DB_0);  // 0dB attenuation for full-scale range

    while (1)
    {
        int adc_value = adc1_get_raw(ADC_CHANNEL);
        ESP_LOGI("ADC", "ADC Value: %d", adc_value);
        vTaskDelay(500 / portTICK_PERIOD_MS);
    }
}
```

**Key Concepts:**

- ADC configuration (`adc1_config_width`, `adc1_config_channel_atten`)
- Reading ADC values (`adc1_get_raw`)

---

### 6. **Wi-Fi Basic Connection (Station Mode)**:

Set up Wi-Fi on the ESP32 to connect to a network in station mode (client mode).

```c
#include "esp_wifi.h"
#include "esp_log.h"
#include "nvs_flash.h"

#define WIFI_SSID "your_SSID"
#define WIFI_PASSWORD "your_PASSWORD"

void app_main(void)
{
    ESP_ERROR_CHECK(nvs_flash_init());
    tcpip_adapter_init();
    ESP_ERROR_CHECK(esp_event_loop_create_default());

    wifi_init_config_t cfg = WIFI_INIT_CONFIG_DEFAULT();
    ESP_ERROR_CHECK(esp_wifi_init(&cfg));

    wifi_config_t wifi_config = {
        .sta = {
            .ssid = WIFI_SSID,
            .password = WIFI_PASSWORD,
        },
    };
    ESP_ERROR_CHECK(esp_wifi_set_mode(WIFI_MODE_STA));
    ESP_ERROR_CHECK(esp_wifi_set_config(ESP_IF_WIFI_STA, &wifi_config));
    ESP_ERROR_CHECK(esp_wifi_start());

    ESP_LOGI("Wi-Fi", "Connecting to Wi-Fi...");
}
```

**Key Concepts:**

- Initializing Wi-Fi (`esp_wifi_init`, `esp_wifi_set_mode`)
- Connecting to Wi-Fi (`esp_wifi_set_config`, `esp_wifi_start`)

---

### 7. **Simple UART Communication**:

Using UART (Universal Asynchronous Receiver/Transmitter) to send and receive data via serial communication.

```c
#include "driver/uart.h"
#include "esp_log.h"

#define UART_PORT_NUM      1
#define UART_BAUD_RATE     115200
#define UART_BUFFER_SIZE   1024

void app_main(void)
{
    uart_config_t uart_config = {
        .baud_rate = UART_BAUD_RATE,
        .data_bits = UART_DATA_BITS_8,
        .parity    = UART_PARITY_DISABLE,
        .stop_bits = UART_STOP_BITS_1,
        .flow_ctrl = UART_HW_FLOWCTRL_DISABLE
    };

    uart_param_config(UART_PORT_NUM, &uart_config);
    uart_driver_install(UART_PORT_NUM, UART_BUFFER_SIZE, UART_BUFFER_SIZE, 0, NULL, 0);

    uint8_t data[] = "Hello, ESP32 UART!\n";
    uart_write_bytes(UART_PORT_NUM, (const char*)data, sizeof(data));

    while (1)
    {
        uint8_t rx_data[128];
        int len = uart_read_bytes(UART_PORT_NUM, rx_data, sizeof(rx_data), 20 / portTICK_PERIOD_MS);
        if (len > 0) {
            uart_write_bytes(UART_PORT_NUM, (const char*)rx_data, len);
        }
    }
}
```

**Key Concepts:**

- UART configuration (`uart_param_config`)
- Sending and receiving data via UART (`uart_write_bytes`, `uart_read_bytes`)

---

### 8. **Timer Interrupt**:

Set up a simple timer interrupt to periodically execute a function.

```c
#include "esp_timer.h"
#include "esp_log.h"

static void timer_callback(void* arg)
{
    ESP_LOGI("Timer", "Timer interrupt triggered!");
}

void app_main(void)
{
    esp_timer_handle_t timer;
    esp_timer_create_args_t timer_args = {
        .callback = timer_callback,
        .name = "timer"
    };

    esp_timer_create(&timer_args, &timer);
    esp_timer_start_periodic(timer, 1000000);  // Trigger every 1 second (1,000,000 us)

    while (1) {
        // Main loop can do other tasks
    }
}
```

**Key Concepts:**

- Timer interrupt setup (`esp_timer_create`, `esp_timer_start_periodic`)
- Timer callback function

---

These examples cover the most basic yet essential concepts when starting with ESP32, and they are reusable in almost every embedded project. As you continue learning, you can expand on these examples and add complexity, such as adding Bluetooth, using SPI/I2C communication, or handling advanced sensor interactions.