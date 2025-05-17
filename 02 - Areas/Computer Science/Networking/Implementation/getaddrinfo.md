Helps setup structs we will use later on. Conducts [[DNS]] and [[Server]] lookup for you as well as populates the `struct sockaddr_in6`. 

```c
int getaddrinfo( 
	const char* node, 
	const char* service,
	const struct addrinfo* hints, 
	const addrinfo** res,
);
```

- `node`: host name to connect to, or an IP address. 
- `service`: can be a port or the name of a particular service like `http` or `ftp`.
- `hints`: pointer to a struct you already filled out with relevant information. 


#### Example Code
___

```c
int main() {
    int status;
    struct addrinfo hints;
    struct addrinfo *servinfo; // will point to the results

    // Make sure the struct is empty
    memset(&hints, 0, sizeof hints);
    hints.ai_family = AF_UNSPEC;     // Don't care if IPv4 or IPv6
    hints.ai_socktype = SOCK_STREAM; // TCP stream sockets
    hints.ai_flags = AI_PASSIVE;     // Fill in my IP for me

    // Get address information
    if ((status = getaddrinfo(NULL, "3490", &hints, &servinfo)) != 0) {
        fprintf(stderr, "getaddrinfo error: %s\n", gai_strerror(status));
        exit(1);
    }

    // servinfo now points to a linked list of 1 or more struct addrinfos

    // Free the linked-list when done
    freeaddrinfo(servinfo);

    return 0;
}
```

----
Tags : #Networking #system-design 