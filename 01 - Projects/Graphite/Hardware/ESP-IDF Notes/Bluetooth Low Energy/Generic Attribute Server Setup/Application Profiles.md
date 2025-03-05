We then implement Application Profiles to handle requests made by the client to the Bluetooth Stack from the Application Layer . We can think of Application Profiles like Classes which have member variables, and interface , and methods which can be accessed by the user .  Each profile is seen as an independent BLE service . It is up to the client to discriminate the services that it is interested in . 

#### Implementation Example 
____
Each profile is defined as a struct where the members depend on the services and characteristics that are implemented . The members also include a [[GATT Interface]] , [[Application ID]] , and a callback function to handle profile events . In this specific example , each profile is composed by .. 

```c
struct gatts_profile_inst {
    esp_gatts_cb_t gatts_cb         ; // Callback Function 
    uint16_t gatts_if               ; // GATTS Interface
    uint16_t app_id                 ; // Application ID 
    uint16_t conn_id                ; // Connection ID 
    uint16_t service_handle         ; // Service Handle
    esp_gatt_srvc_id_t service_id   ; // Service ID
    uint16_t char_handle            ; // Characteristic Handle
    esp_bt_uuid_t char_uuid         ; // Characteristic UUID
    esp_gatt_perm_t perm            ; // Attribute Permission 
    esp_gatt_char_prop_t property   ; // Characteristic Property
    uint16_t descr_handle           ; // Client Characteristic Configuration Descriptor
    esp_bt_uuid_t descr_uuid        ; // Client Characteristic Configuraiton UUID
};
```


This profile has was designed to have one service and one characteristic , and that the characteristic has one descriptor . Note that the characteristic supports notification or indications, it must implement a client characteristic configuration descriptor ( This ties into the fact that Bluetooth Devices can act as both clients and server ) . which is an additional attribute that describes if the notifications or indications are enabled and defines how the characteristic may be configured by a specific client. This descriptor also has a handle and an UUID.
#### Storing Application Profiles
___
The Application Profiles are stored in an array and corresponding callback functions `gatts_profile_a_event_handler()` and `gatts_profile_b_event_handler()` are assigned. Different applications on the GATT client use different interfaces, represented by the gatts_if parameter. For initialization, this parameter is set to `ESP_GATT_IF_NONE`, which means that the Application Profile is not linked to any client yet.
____
Tags : #programming #computer-architecture #graphite