> [!abstract] tldr
>  Function Used to create timers  , defined in `esp_timer.h`

#### Arguments 
____
> [!info] &esp_timer_create_args_t
> `Pointer to Configuration struct` which has the following attributes ...
> `.callback`:  a function to call whenever a tick happens . 
> `.arg` : arguments being passed to the callback function 
> `.name` : Name of the timer 


> [!note] &esp_timer_handle_t
>  `Pointer` to a `handle` to a timer created using the ESP-IDF software timer APIs`


____
Tags : #programming #computer-architecture #graphite