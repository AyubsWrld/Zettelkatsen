```c
typedef struct {
    bool dev_found;                                  // Stores whether the device has been found or not
    uint8_t bdname_len;                              // Stores bluetooth device's name length
    uint8_t eir_len;                                 // Stores
    uint8_t rssi;                                    // Stores
    uint32_t cod;                                    // Stores
    uint8_t eir[ESP_BT_GAP_EIR_DATA_LEN];            // Stores
    uint8_t bdname[ESP_BT_GAP_MAX_BDNAME_LEN + 1];   // Stores
    esp_bd_addr_t bda;                               // Stores
    app_gap_state_t state;                           // Struct for State of the bluetooth device
} app_gap_cb_t;
```
____
Tags : #programming #computer-architecture #graphite