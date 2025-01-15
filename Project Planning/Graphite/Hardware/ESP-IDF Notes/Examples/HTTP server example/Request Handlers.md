### root_handler
___
- **Purpose** : Handles Logic for `/` directory

```c
static esp_err_t root_handler(httpd_req_t *req)
{
    httpd_resp_send(req, html_page, strlen(html_page));
    return ESP_OK;
}
```

### data_handler
___
- **Purpose** : Handles Logic for 

```c
static esp_err_t data_handler(httpd_req_t *req)
{
    // Example: sending a simulated temperature value
    char resp[32];
    sprintf(resp, "23.5");
    httpd_resp_send(req, resp, strlen(resp));
    return ESP_OK;
}
```

### toggle_handler
___

- **Purpose** : Handles Logic for 

```c
static esp_err_t toggle_handler(httpd_req_t *req)
{
    static bool led_state = false;
    led_state = !led_state;
    gpio_set_level(LED_PIN, led_state);
    httpd_resp_send(req, "OK", 2);
    return ESP_OK;
}
```

____
Tags : #programming #computer-architecture #graphite