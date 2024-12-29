After the [[Application Profiles]] have been created we can store them using [[Statically Allocated Arrays]] .  First we define the position of the profile and store it within an array .. 
```c
#include <stdio.h>
#include <string.h> 

#define EXIT_SUCCESS 0
#define ESP_GATT_IF_NONE "NULL"
#define PROFILE_NUM 2
#define PROFILE_A_APP_ID 0
#define PROFILE_B_APP_ID 1
#define PROFILE_C_APP_ID 2


struct gatts_profile_inst {
    char* (*gatts_cb)(void);
    char* gatts_if;
};


char* cb(){
  return "Callback" ;
}

static struct gatts_profile_inst gl_profile_tab[PROFILE_NUM] = {
    [PROFILE_A_APP_ID] = {
        .gatts_cb = &cb,
        .gatts_if = ESP_GATT_IF_NONE,       
    },
    [PROFILE_B_APP_ID] = {
        .gatts_cb = &cb,
        .gatts_if = ESP_GATT_IF_NONE,       
    },
    [PROFILE_C_APP_ID] = {
        .gatts_cb = &cb,
        .gatts_if = ESP_GATT_IF_NONE,       
    },
};




int main(){
  printf("%s" , gl_profile_tab[0].gatts_cb()) ; 
  return EXIT_SUCCESS ;
}

```

Then we register the Application Profiles .. 
```c
esp_ble_gatts_app_register(PROFILE_A_APP_ID) ; 
esp_ble_gatts_app_register(PROFILE_B_APP_ID) ; 
```
___
Tags : #programming #graphite 