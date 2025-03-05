After we have setup the Bluetooth Stack , we must define what happens when a client interacts with the Bluetooth Server . To do this , we instantiate callback functions . The two main handlers of these callback functions , also referred to as event handlers are the [[gap_event_handler]] and [[gatts_event_handler]] . The application needs to register a callback function for each event handler in order to let the application know which functions are going to handle the GAP and GATT events

```c
esp_ble_gatts_register_callback(gatts_event_handler);
esp_ble_gap_register_callback(gap_event_handler);
```

The functions `gatts_event_handler()` and `gap_event_handler()` handle all the events that are pushed to the application from the BLE stack.
____
Tags : #programming #computer-architecture #graphite