Allows for communication between services in a language agnostic way. 

```
+----------------+
| Client         |
|  +----------+  |         +---------------+
|  |   main   |  |         | Server        |
|  |----------|  |         |  +----------+ |
|  | stub_cli |----(comms)--->| stub_svr | |
|  +----------+  |         |  |----------| |
+----------------+         |  | function | |
                           |  +----------+ |
                           +---------------+
```

