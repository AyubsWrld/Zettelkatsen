-  `#include <string.h>` : 
-  `#include <freeRTOS.h>` :  Task scheduling manager ( Like task scheduling and task priorities ) .  
-  `#include <task.h>`: Provides API's for task management ( `xTaskCreate` , `vTaskDelay` )  . 
-  `#include <esp_wifi.h>` :  Library for Wi-Fi driver API's , enabling configuration , connection , and control of Wi-Fi Features . 
-  `#include <esp_system.h>` : Allows us to retrieve system-level information like retrieving chip information , resetting the device , and getting unique device IDs . 
-  `#include <esp_event.h>`:  Offers the event loop library for handling asynchronous events . 
-  `#include <esp_log.h>`: For logging 
-  `#include <nvs_flash.h>`: For setting up and utilizing Non-Volatile Memory . 
-  `#include <lwip.h/err.h>`: Defines error codes and functions related to the lightweight IP stack
-  `#include <lwip/sys.h>`: Provides system abstraction functions for the LWIP stack , like timers and mutexes . 
-  `#include <esp_http_server.h>`: Contains APIs for creating an HTTP server, Handling Client Request , and sending HTTP responses . 
-  `#include <driver/gpio.h>`: Provides APIs for controlling the General Purpose Input/Output (GPIO) pins , allowing you to read or write to pins for hardware interfacing . 
____
Tags : #programming #computer-architecture #graphite