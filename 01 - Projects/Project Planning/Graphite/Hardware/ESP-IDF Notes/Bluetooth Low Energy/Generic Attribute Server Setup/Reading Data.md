Within the switch statement defined in `esp_profile_a_event_handler()` , we have a case which responds to the **Gatts** event `ESP_GATTS_READ_EVT` . This is the case wherein the **Central** Device has requested to read some data .. 
### Response Structure
___
We begin by logging when the `ESP_GATTS_READ_EVT` is received . 

```c
    case ESP_GATTS_READ_EVT: {
        ESP_LOGI(GATTS_TAG, "Characteristic read, conn_id %d, trans_id %" PRIu32 ", handle %d", param->read.conn_id, param->read.trans_id, param->read.handle);
```

Next we prepare our response to the **Central Device**  . Here we utilize an `esp_gatt_rsp_t` which holds the GATT attribute value, including its data, handle, and metadata.

```c
        esp_gatt_rsp_t rsp;
        memset(&rsp, 0, sizeof(esp_gatt_rsp_t));
        rsp.attr_value.handle = param->read.handle;
        rsp.attr_value.len = 4;
        rsp.attr_value.value[0] = 0xde;
        rsp.attr_value.value[1] = 0xed;
        rsp.attr_value.value[2] = 0xbe;
        rsp.attr_value.value[3] = 0xef;
        esp_ble_gatts_send_response(gatts_if, param->read.conn_id, param->read.trans_id,
                                    ESP_GATT_OK, &rsp);
        break;
    }

```

### Response Structure
___
### `esp_gatt_rsp_t` **rsp** 

- **Purpose** : represents the response type for a GATT remote read request.
- **Members** ..
	- `esp_gatt_value_t attr_value` : he GATT attribute value, including its data, handle, and metadata.
	- `uint16_t` : Only the handle of the GATT attribute, when that's the only required information.
### `esp_gatt_value_t` attr_value
- **Purpose** : Represents a GATT attribute's value.
- **Members** : We only concern ourselves with the `.value` & `.len` to set data within the array and the current length of the data in the value array respectively . for more see the entire [Struct Implementaiton](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/bluetooth/esp_gatt_defs.html#_CPPv416esp_gatt_value_t "Permalink to this definition")
	
____ 
Tags : #programming #computer-architecture #graphite