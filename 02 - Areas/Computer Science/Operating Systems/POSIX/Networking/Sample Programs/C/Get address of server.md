```c


#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netdb.h>
#include <arpa/inet.h>
#include <netinet/in.h>


int main( int argc, char* argv[] )
{

  if( argc != 2 ) {
    fprintf(stderr, " Usage: [ HOSTNAME ]\n" ) ;
    exit(EXIT_FAILURE) ;
  }

  struct addrinfo hints, *res, *p;
  int status; 
  char ipstr[INET6_ADDRSTRLEN] ;

  memset(&hints, 0, sizeof(hints) ); 

  hints.ai_family = AF_INET6      ; 
  hints.ai_socktype = SOCK_STREAM ; 

  if( (status = getaddrinfo(argv[1], NULL, &hints, &res)) != 0 ){
    fprintf( stderr, "getaddrinfo: %s\n", gai_strerror(status));
    exit(EXIT_FAILURE); 
  }

  printf("IP Addresses for %s:\n\n", argv[1]) ; 

  for( p = res; p != NULL ; p = p->ai_next ) {

    void *addr ; 
    char *ipver;

    struct sockaddr_in6 *ipv6 = ( struct sockaddr_in6 *) p->ai_addr ; 

    addr = &(ipv6->sin6_addr);
    ipver = "IPv6" ; 


    inet_ntop( p->ai_family, addr, ipstr, sizeof(ipstr));
    printf( " %s: %s\n", ipver, ipstr );
  }

  freeaddrinfo(res) ; 

  return EXIT_SUCCESS  ;

}

```

----

Tags : #Networking #system-design 