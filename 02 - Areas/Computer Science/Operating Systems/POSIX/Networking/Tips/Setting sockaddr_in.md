```cpp
struct sockaddr_in sock_address = {
    .sin_family = AF_INET, 
    .sin_port = htons( 4090 ), 
    .sin_addr = { .s_addr = inet_addr("127.0.0.1") },
    .sin_zero = { 0 } 
};
```

Here we hardcode everything ourselves. 

- `.sin_fmaily` is our address family. 
- `.sin_port` is our port number. We use [[htons]] to go from little endian ( what are intel CPU uses ) to big endian which is what networks use. 
- `.sin_addr` is of type `in_addr` which has the `s_addr` field we have to place the IP address in. 
- `.sin_zero` is the padding we must throw is after. 

----

Tags : #Networking #system-design 