Some configurations can be simply initialized with their default values ( Using Designated Initialization ) . The values can be changed after . 

```c
httpd_config_t config = HTTPD_DEFAULT_CONFIG();
/* HTTPD_DEFAULT_CONFIG expands to a designated initializer. Now all fields are set to the default values, and any field can still be modified: */
config.server_port = 8081;
httpd_handle_t server;
esp_err_t err = httpd_start(&server, &config);
```

It is recommended to use default initializer macros whenever they are provided for a particular configuration structure.

____
Tags : #programming #computer-architecture #graphite