Used to logically connect a packet to the [[Socket Descriptor]] we got from using `socket()`. Used so that we can `listen()` and wait for the kernel to send our process the packet once it knows the packet was meant for our process ( using the port number ). 

> *Bind maps packets to processes.*


```c
int bind( int sockfd, struct sockaddr *my_addr, int addrlen ) ;
```

#### Example
___

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netdb.h>

int main() {
    struct addrinfo hints, *res;
    int sockfd;

    // First, load up address structs with getaddrinfo()
    memset(&hints, 0, sizeof hints);
    hints.ai_family = AF_UNSPEC;    // Use IPv4 or IPv6, whichever
    hints.ai_socktype = SOCK_STREAM;
    hints.ai_flags = AI_PASSIVE;    // Fill in my IP for me

    // Get address information
    if (getaddrinfo(NULL, "3490", &hints, &res) != 0) {
        perror("getaddrinfo error");
        exit(1);
    }

    // Make a socket
    sockfd = socket(res->ai_family, res->ai_socktype, res->ai_protocol);
    if (sockfd == -1) {
        perror("socket error");
        exit(1);
    }

    // Bind it to the port we passed in to getaddrinfo()
    if (bind(sockfd, res->ai_addr, res->ai_addrlen) == -1) {
        perror("bind error");
        exit(1);
    }

    // Free the linked-list when done
    freeaddrinfo(res);

    return 0;
}

```
----

Tags : #Networking #system-design 