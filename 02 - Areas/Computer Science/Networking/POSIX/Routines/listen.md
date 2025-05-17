```c
int listen( int sockfd, int backlog ) ;
```

#### Purpose: 
-  **listen**() marks the socket referred to by `sockfd` as a passive socket, that is, as a socket that will be used to accept incoming connection requests using [[accept]]
#### Return: 
- `0`: Success.
- `-1`: Error, [[errno]] is set to indicate the error. 

----

Tags : #Networking #system-design 