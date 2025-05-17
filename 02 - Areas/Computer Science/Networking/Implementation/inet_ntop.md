Converts to binary IPv4/IPv6 Address to readable text format. 
**Network to presentation.**

#### IPv4

```c
#include <arpa/inet.h>
#include <stdio.h>



int main()
{
  char ip4[INET_ADDRSTRLEN] ; 
  struct sockaddr_in sa; 

  inet_ntop( AF_INET, &(sa.sin_addr), ip4, INET_ADDRSTRLEN ) ; 

  printf("The IPv4 Address is: %s\n", ip4 ) ;
  return 0 ;
}
```

#### IPv6

```c
#include <netinet/in.h>


int main()
{
  char ip6[INET6_ADDRSTRLEN] ; 
  struct sockaddr_in6 sa; 

  inet_ntop( AF_INET, &(sa.sin6_addr), ip6, INET_ADDRSTRLEN ) ; 

  printf("The IPv6 Address is: %s\n", ip6 ) ;
  return 0 ;
}

```


----
Tags : #Networking #system-design 