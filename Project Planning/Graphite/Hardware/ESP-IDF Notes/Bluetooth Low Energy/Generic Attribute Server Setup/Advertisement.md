After we have created and stored the [[Project Planning/Graphite/Hardware/ESP-IDF Notes/Bluetooth Low Energy/Profiles/Application Profiles|Application Profiles]] , we can now broadcast our BLE service through doing the following .. 

#### Advertising the Data 
___
  1. **Defining the Advertisement Data**:
    - When the application registers (via `ESP_GATTS_REG_EVT`), this event is used to set the advertisement parameters and the device name.
      
2. **Registering the Application**:
	- When the application registers (via `ESP_GATTS_REG_EVT`), this event is used to set the advertisement parameters and the device name.
3. **Setting Advertising Data**:
    - Advertisement data can either use standard formats or custom raw formats, depending on the `CONFIG_SET_RAW_ADV_DATA` macro.
4. **Handling Advertisement Size Limits**:
    - BLE advertisements have a size limit (31 bytes). Parameters exceeding this limit will be truncated unless managed carefully.
____
Tags : #programming #computer-architecture #graphite