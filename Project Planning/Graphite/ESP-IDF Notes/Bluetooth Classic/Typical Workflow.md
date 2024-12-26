#### 1. **Initialize the Bluetooth Stack**

- Initialize NVS (Non-Volatile Storage), required by the Bluetooth stack.
- Initialize and enable the Bluetooth controller and Bluedroid stack.

#### 2. **Configure GAP**

- Set the device name using `esp_bt_dev_set_device_name()`.
- Make the device discoverable and connectable using `esp_bt_gap_set_scan_mode()`.

#### 3. **Set Up the Desired Profile**

- For serial communication, initialize the SPP profile with `esp_spp_init()`.
- Register a callback function to handle SPP events like data reception.

#### 4. **Start the Profile Server**

- Start an SPP server using `esp_spp_start_srv()`.

#### 5. **Handle Events**

- Use callbacks to handle events like data reception, connection establishment, and disconnection.

#### 6. **Send/Receive Data**

- Use `esp_spp_write()` to send data to a connected device.
____
Tags : #programming #computer-architecture #graphite