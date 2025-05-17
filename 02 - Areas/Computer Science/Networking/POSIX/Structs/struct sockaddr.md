```c
struct sockaddr{ 
	unsigned short    sa_family   ;  // Address family AF_xxx
	char              sa_data[14] ;  // 14 bytes of protocol address
};
```

#### **Purpose**:
- holds socket address information for many types of sockets. Describes a socket address. 
#### **Members**:
- `sa_family`: can be a variety of things. `sa_data` contains a destination address and port number for the socket. 
- `sa_data`: Socket pathname. 

To deal with struct `sockaddr`, programmers created a parallel structure: struct `sockaddr_in`.

a pointer to a struct `sockaddr_in` can be cast to a pointer to a `struct sockaddr`, this relationship is commutative. This becomes useful because `connect()` expects a `struct sockaddr*` but you can cast it at last minute. 



----

Tags : #Networking #system-design 