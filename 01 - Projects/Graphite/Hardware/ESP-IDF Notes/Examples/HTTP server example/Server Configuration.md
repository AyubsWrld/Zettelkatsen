```c
// HTTP server configuration
httpd_uri_t uri_root = {
    .uri = "/",
    .method = HTTP_GET,
    .handler = root_handler,
    .user_ctx = NULL
};
```

```c
httpd_uri_t uri_data = {
    .uri = "/data",
    .method = HTTP_GET,
    .handler = data_handler,
    .user_ctx = NULL
};
```

```c
httpd_uri_t uri_toggle = {
    .uri = "/toggle",
    .method = HTTP_GET,
    .handler = toggle_handler,
    .user_ctx = NULL
};
```
____
Tags : #programming #computer-architecture #graphite