Accessing data through a pointer of a different type. 

```c
struct sockaddr {
	unsigned short sa_family   ; // Socket Address Family 
	char           sa_data[14] ; // Memory Pool.
}

struct __attribute_struct_may_alias__ sockaddr_in
  {
    __SOCKADDR_COMMON (sin_);
    uint16_t    sin_port;			/* Port number.  2 bytes */*
    struct in_port_t sin_addr;		/* Internet address.  */

    /* Pad to size of `struct sockaddr'.  */
    unsigned char sin_zero[sizeof (struct sockaddr)
		   - __SOCKADDR_COMMON_SIZE
		   - sizeof (in_port_t)
		   - sizeof (struct in_addr)];
  };

```
___
Tags : #programming #cpp 