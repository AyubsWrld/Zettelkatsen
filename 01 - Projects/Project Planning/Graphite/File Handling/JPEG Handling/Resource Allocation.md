Create [[JPEG Decoder Engine]] which is initialized utilizing an initialization struct . We also create a handle to pass to the initialization function so that we may reference the [[JPEG Decoder Engine]] later . 
```c
jpeg_decoder_handle_t decoder_engine;

jpeg_decode_engine_cfg_t decode_eng_cfg = {
    .intr_priority = 0,
    .timeout_ms = 40,
};

ESP_ERROR_CHECK(jpeg_new_decoder_engine(&decode_eng_cfg, &decoder_engine));
```

Whenever the engines is no longer needed we can delete it   . 

```c
ESP_ERROR_CHECK(jpeg_del_decoder_engine(decoder_engine));
```

The same goes for initializing and deleting the resources for a jpeg encoder engine 

```c
jpeg_encoder_handle_t encoder_engine;

jpeg_encode_engine_cfg_t encode_eng_cfg = {
    .intr_priority = 0,
    .timeout_ms = 40,
};

ESP_ERROR_CHECK(jpeg_new_encoder_engine(&encode_eng_cfg, &encoder_engine));
```

____
Tags : #programming #computer-architecture #graphite