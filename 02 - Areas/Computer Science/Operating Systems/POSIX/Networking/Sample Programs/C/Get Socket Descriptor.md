```c
int s ;
stuct addrinfo hints, *res ; 

// Do error handling here. Also assumes that hints is zeroed out. 
getaddrinfo( "www.example.com", "http", &hints, &res ) ; 

s = socket( res->ai_family, res->ai_socktype, res->ai_protocol ) ; 
```

----

Tags : #Networking #system-design 