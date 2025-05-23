```c
#include <sys/socket.h> 
int socket(int domain, int type, int protocol);
```

#### Purpose :
- [[System Call]] issued to the kernel to allocate a buffer and return a [[Socket Descriptor]]. 
#### Arguments :
- `domain`: Sockets that share common communication properties, such as naming conventions and protocol address formats, are grouped into _communication_ _domains_. A communication domain is sometimes referred to as name or address space. This would be like your IPv4 and IPv6 addresses.
- `type`: specifies communication semantics( TCP , UDP ). 
- `protocol`: specifies the particular protocol to be used with the socket. 

#### Return :
- `sfd`: [[Socket Descriptor]] returned from the [[System Call]]. Maps to an entry in the processes file table -> kernels Open File Table -> Memory buffer to move data from network peripheral. 
- `-1`: Error, [[errno]] is set to indicate the error. 



   
   
----
Tags : #Networking #system-design 