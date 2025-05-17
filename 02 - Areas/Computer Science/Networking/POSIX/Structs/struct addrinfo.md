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

----
Tags : #Networking #system-design 