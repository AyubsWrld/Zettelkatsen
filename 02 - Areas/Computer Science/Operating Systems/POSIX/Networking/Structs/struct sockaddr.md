```c
struct sockaddr{ 
	unsigned short    sa_family   ;  // Address family AF_xxx
	char              sa_data[14] ;  // 14 bytes of protocol address
};
```

#### **Purpose**:
- Stores information regarding the [[Socket Address]]. `sa_data` is a [[Generic Memory Pool]] used to store the information relating to the socket address, It's interpretation relies on the `sa_family`. 
- This is a [[Generic Type]] which we don't usually use to pass into functions. It is usually casted to some other similar struct for use in functions. 
#### **Members**:
- `sa_family`: Stores [[Address Family]] Information, Like [[AF_INET]] for IPv4 or [[AF_INET6]] for IPv6. This is also used to interpret 
- `sa_data`: Stores information about the [[IP Address]] and [[Port]]. However its interpretation is dependent on `sa_family`. 

To deal with struct `sockaddr`, programmers created a parallel structure: struct `sockaddr_in`.

a pointer to a struct `sockaddr_in` can be cast to a pointer to a `struct sockaddr`, this relationship is commutative. This becomes useful because `connect()` expects a `struct sockaddr*` but you can cast it at last minute. 




----

Tags : #Networking #system-design 