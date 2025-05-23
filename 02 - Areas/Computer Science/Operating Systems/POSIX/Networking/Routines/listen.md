```c
int listen( int sockfd, int backlog ) ;
```

#### Purpose: 
-  **listen**() marks the socket referred to by `sockfd` as a passive socket, that is, as a socket that will be used to accept incoming connection requests using [[accept]]

#### Arguments: 
- `sockfd`: Socket file descriptor from the `socket()` system call. 
- `backlog`: Number of connections allowed on the incoming queue. incoming connections are going to wait in this queue until you accept() them. This limit is how many can queue up. 
#### Purpose: 
- `0`: Success.
- `-1`: Error, [[errno]] is set to indicate the error. 

----

Tags : #Networking #system-design 