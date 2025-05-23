Instead of using `perror()` or `strerror` we can utilize a macro to hold the boilerplate instead of having to write it out every single time. 

```cpp
#define CHECK(X) ({int __val = (X); (__val == -1 ? \
    ({fprintf(stderr, "ERROR (" __FILE__ ":%d) -- %s\n", __LINE__, strerror(errno)); \
    exit(-1); -1;}) : __val); })
```
_____
Tags : #operating-systems #posix #errors 
