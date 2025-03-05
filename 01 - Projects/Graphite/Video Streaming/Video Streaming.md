- **Why can't we just use the ESP32 to generate HLS packets?** It's unrealistic because the ram of the board ( *512 kbs* ) is far too small to even hold a singular [[Transport Stream File]] . The sdcard read write speeds are far too slow . 
- **ESP32** sends raw video to mobile device via TCP connection . 
- **User Device** receives raw data and converts it to [[RTMP]] and streams it . ( Slow ) ? 
- **Work Arounds** : We can store the videos as HSL segments using ffmpeg . ( How can we revert them back? )  .  This requires preprocessing the files , which uses the computational power of the phone as opposed to the computational power of the **ESP32**which circumvents the need to utilize the **ESP32**s computational resources 
- 
____
Tags : #programming #computer-architecture #graphite
