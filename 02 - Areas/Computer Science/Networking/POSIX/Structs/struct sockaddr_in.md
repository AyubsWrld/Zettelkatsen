```c
// ( IPv4 only -- see struct sockaddr_in6 for IPv6 ) 

struct sockaddr_in {
	short int               sin_family ; // Address Family, AF_INET
	unsigned short int      sin_port   ; // Port number
	struct in_addr          sin_addr   ; // Internet Address
	unsigned char           sin_zero[8] ; // same size as struct sockaddr
}
```

This structure makes it easy to reference elements of the socket address.

- `sin_zero`: should be set to all zeros with the function `memset()`. 
 
- `sin_family`: AF_INET( IPv4 ) or AF_INET6( IPv6 ) although IPv6 utilizes `sockaddr_in6` struct. 
  
- `sin_port`: must be in Network Byte Order ( [[Big-Endian]]) by using `htons()`; 
  
- `in_addr`: Internet address union. 
----

Tags : #Networking #system-design 