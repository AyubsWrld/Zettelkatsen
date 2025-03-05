

```c
// Function to handle root URL
static esp_err_t root_handler(httpd_req_t *req)
{
    httpd_resp_send(req, html_page, strlen(html_page));
    return ESP_OK;
}```
____
Tags : #programming #computer-architecture #graphite