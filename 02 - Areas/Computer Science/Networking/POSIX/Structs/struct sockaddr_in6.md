```c

struct sockaddr_in6 {
    uint16_t sin6_family;   // Address family, AF_INET6
    uint16_t sin6_port;     // Port number, Network Byte Order
    uint32_t sin6_flowinfo; // IPv6 flow information
    struct in6_addr sin6_addr; // IPv6 address
    uint32_t sin6_scope_id; // Scope ID
};

```

----

Tags : #Networking #system-design 