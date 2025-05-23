```c
int bind( int sockfd, const struct sockaddr *addr, socklen_t addrlen ); 
```

#### Purpose: 
- When a socket is created with [[socket]], the kernel is aware of it however it is not tied to our process. `bind()` assigns the address specified by `addr` to the socket referred to by the [[Socket Descriptor]] `sockfd`. This process is called "assigning a name to a socket" 

#### Parameter: 
- `sockfd`: [[Socket Descriptor]] to bind the address to. 
- `addr`: info pertaining to the socket. 
- `addrlen`: size of the `addr` struct. 

#### Return: 
- `0`: Success.
- `-1`: Error, [[errno]] is set to indicate the error. 
----
Tags : #Networking #system-design 