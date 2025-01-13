	The **Generic Access Profile** controls connection and advertising in Bluetooth . Gap is what makes your device visible to the outside world , and determines how two devices can ( or can't ) interact with one another . 

### Device Roles
___
GAP defines various roles for devices , but the two key concepts to keep in mind are **Central** devices and **Peripheral** Devices . 
- **Central Devices** : Devices being used to connect to the Bluetooth Device 
- **Peripheral** : lightweight devices with lower power affinity which connect to a much stronger **Central Device** . 

### Advertising and Scan Response Data
___
There are two main ways to send advertising out with **GAP** , the **Advertising Data Payload** and the **Scan Response** Payload . Both of these payloads are identical and can send up to 31 bytes ( *248 bits* ) of data . but only the advertising data payload is mandatory , since it's the data which needs to be sent out to let the **Central Devices** know that it exists . The **Scan Response Payload** is supplementary data which we as developers can utilize to send extra details about our peripheral device which is being advertised , such as strings for a *Device Name* . 

### The Advertising Process
___
The **Peripheral Device** defines an **Advertisement Interval** wherein a **Advertising Data Payload** is sent at the beginning of every **Advertisement Interval** . There exists a tradeoff between how often the **Advertising Data Payload** with respect to battery efficiency . The more often the payload is sent the more responsive the **Peripheral Device** feels , at of course , the expense of battery life .  


### Advertising Payload Data struct
___
We define the Advertising Data Payload utilizing a `C-style Struct` with the following attributes . 

```c
typedef struct {
    bool set_scan_rsp;            /*!< Set this advertising data as scan response or not*/
    bool include_name;            /*!< Advertising data include device name or not */
    bool include_txpower;         /*!< Advertising data include TX power */
    int min_interval;             /*!< Advertising data show slave preferred connection min interval */
    int max_interval;             /*!< Advertising data show slave preferred connection max interval */
    int appearance;               /*!< External appearance of device */
    uint16_t manufacturer_len;    /*!< Manufacturer data length */
    uint8_t *p_manufacturer_data; /*!< Manufacturer data point */
    uint16_t service_data_len;    /*!< Service data length */
    uint8_t *p_service_data;      /*!< Service data point */
    uint16_t service_uuid_len;    /*!< Service uuid length */
    uint8_t *p_service_uuid;      /*!< Service uuid array point */
    uint8_t flag;                 /*!< Advertising flag of discovery mode, see BLE_ADV_DATA_FLAG detail */
} esp_ble_adv_data_t;
```

Here is an example of an instance of the struct 
```c
static esp_ble_adv_data_t adv_data = {
    .set_scan_rsp = false,
    .include_name = true,
    .include_txpower = true,
    .min_interval = 0x0006,
    .max_interval = 0x0010,
    .appearance = 0x00,
    .manufacturer_len = 0, //TEST_MANUFACTURER_DATA_LEN,
    .p_manufacturer_data =  NULL, //&test_manufacturer[0],
    .service_data_len = 0,
    .p_service_data = NULL,
    .service_uuid_len = 32,
    .p_service_uuid = test_service_uuid128,
    .flag = (ESP_BLE_ADV_FLAG_GEN_DISC | ESP_BLE_ADV_FLAG_BREDR_NOT_SPT),
};
```


### Initiating Advertisement 
___
After we have defined the **Advertising Data Payload** , we can now begin to advertise our **Peripheral Device** by utilizing the `gatts_profile_a_event_handler()` callback function defined as ..

The Implementation goes as follows ...

**Signature**  `gatts_profile_a_event_handler()` which takes **Parameters** .. 
- `esp_gatts_cb_event_t event`  : **Enumeration Type** Which represents the event
- `esp_gatt_if_t gatts_if` :  Handle used to specify the particular GATT Application Instance
- `esp_ble_gatts_cb_param_t *param)` : pointer to a structure that contains additional data relevant to the event that triggered the callback

handle the **GATT server registration event** by logging relevant data and initializing the service metadata for Profile A, preparing it for subsequent BLE operations.

```c
static void gatts_profile_a_event_handler(esp_gatts_cb_event_t event, esp_gatt_if_t gatts_if, esp_ble_gatts_cb_param_t *param) {
    switch (event) {
    case ESP_GATTS_REG_EVT:
        ESP_LOGI(GATTS_TAG, "GATT server register, status %d, app_id %d, gatts_if %d", param->reg.status, param->reg.app_id, gatts_if);
        gl_profile_tab[PROFILE_A_APP_ID].service_id.is_primary = true;
        gl_profile_tab[PROFILE_A_APP_ID].service_id.id.inst_id = 0x00;
        gl_profile_tab[PROFILE_A_APP_ID].service_id.id.uuid.len = ESP_UUID_LEN_16;
        gl_profile_tab[PROFILE_A_APP_ID].service_id.id.uuid.uuid.uuid16 = GATTS_SERVICE_UUID_TEST_A;
        ```

Set device name for the **Generic Access Profile** to Advertise within the **Advertising Payload Data** 

```c
        esp_err_t set_dev_name_ret = esp_ble_gap_set_device_name(test_device_name);
        if (set_dev_name_ret){
            ESP_LOGE(GATTS_TAG, "set device name failed, error code = %x", set_dev_name_ret);
        }
```

Set **raw_adv_dat**

```c
#ifdef CONFIG_EXAMPLE_SET_RAW_ADV_DATA
        esp_err_t raw_adv_ret = esp_ble_gap_config_adv_data_raw(raw_adv_data, sizeof(raw_adv_data));
        if (raw_adv_ret){
            ESP_LOGE(GATTS_TAG, "config raw adv data failed, error code = %x ", raw_adv_ret);
        }
        adv_config_done |= adv_config_flag;
        esp_err_t raw_scan_ret = esp_ble_gap_config_scan_rsp_data_raw(raw_scan_rsp_data, sizeof(raw_scan_rsp_data));
        if (raw_scan_ret){
            ESP_LOGE(GATTS_TAG, "config raw scan rsp data failed, error code = %x", raw_scan_ret);
        }
        adv_config_done |= scan_rsp_config_flag;
#else
        //config adv data
        esp_err_t ret = esp_ble_gap_config_adv_data(&adv_data);
        if (ret){
            ESP_LOGE(GATTS_TAG, "config adv data failed, error code = %x", ret);
        }
        adv_config_done |= adv_config_flag;
        //config scan response data
        ret = esp_ble_gap_config_adv_data(&scan_rsp_data);
        if (ret){
            ESP_LOGE(GATTS_TAG, "config scan response data failed, error code = %x", ret);
        }
        adv_config_done |= scan_rsp_config_flag;

#endif
```



____
Tags : #programming #computer-architecture #graphite