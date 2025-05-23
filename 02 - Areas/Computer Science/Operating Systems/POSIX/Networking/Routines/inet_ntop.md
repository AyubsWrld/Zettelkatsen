```c
const char* inet_ntop( 
	int address_family,
	const void *__restrict__src,
	char dest, 
	socklen_t size
	); 
```

#### Purpose: 
- When a socket is created with [[socket]], the kernel is aware of it however it is not tied to our process. `bind()` assigns the address specified by `addr` to the socket referred to by the [[Socket Descriptor]] `sockfd`. This process is called "assigning a name to a socket" 

#### Parameter: 
- `int address_family`: [[Address family]], could be either of [[AF_INET]] or [[AF_INET6]]. This tells `inet_ntop` how to handle `__restrict__src` argument ( I'm inferring its use here ). 
- `const void *__restrict__src`: `sockaddr` struct, holds the data used to actually create the string representation.
- `char dest`: Destination to write the result. 
- `socklen_t size`: size of the buffer.
#### Return: 
   On success, **inet_ntop**() returns a non-null pointer to _dst_.  NULL
   is returned if there was an error, with _[errno](https://www.man7.org/linux/man-pages/man3/errno.3.html)_ set to indicate the error.

#### Example: 

Retrieving the IPv4 Address of google.com. 

```c
#include <cstdlib>
#include <iostream>
#include <sys/socket.h>
#include <netdb.h>
#include <string.h>
#include <netinet/in.h>
#include <arpa/inet.h>

int main()
{
  int status ; 
  char buffer[INET6_ADDRSTRLEN] ;
  struct addrinfo hint, *p; 
  memset( &hint, 0, sizeof(hint) ) ;

  hint.ai_family = AF_INET       ; 
  hint.ai_socktype = SOCK_STREAM ; 

  if (( status = getaddrinfo( "www.google.com", NULL, &hint, &p ) != 0 )){
    fprintf( stderr, "getaddrinfo: %s\n", gai_strerror(status)); 
    exit(EXIT_FAILURE); 
  }

  struct sockaddr_in* x = ( struct sockaddr_in* ) p->ai_addr; 

  inet_ntop( AF_INET, &(x->sin_addr), buffer, INET6_ADDRSTRLEN ); 

  std::cout << buffer << std::endl;
  return EXIT_SUCCESS ; 
}
```
----
Tags : #Networking #system-design 