```c
struct addrinfo {
	int                 ai_flags     ; 
	
	int                 ai_family    ; 
	
	int                 ai_socktype  ; 
	
	int                 ai_protocol  ; 
	
	size_t              ai_addrlen   ; 
	
	struct sock_addr*   ai_flags     ; 
	
	char*               ai_cannonname; 
	
	struct addrinfo*    ai_next      ; 
}
```

- `ai_flags`: Hints for [[getaddrinfo]] such as..
	- `AI_PASSIVE`: Suitable for `bind()`
	- `AI_CANONNAME`: Request canonical name  
	- `AI_NUMERICHOST`: Prevent DNS resolution
- `ai_family`: [[Address Family]], [[AF_INET]]/[[AF_INET6]] ( IPv4, IPv6 ). 
- `ai_socktype`: Stream or DGRAM ( TCP / UDP ).
- `addrlen`: Size of the addrinfo ; 

----
Tags : #Networking #system-design 