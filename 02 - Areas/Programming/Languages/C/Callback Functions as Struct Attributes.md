Used to instantiate callback functions within structs 
- `retval( *nameoffunction)(arguments)`
```c
#include <stdio.h>
#include <string.h> 

#define EXIT_SUCCESS 0


struct Names{
  char* (*cb)(char*);
  char* name ; 
};

char* isEqual(char* cmp){
  if (strcmp(cmp , "Hello") == 0) {
    return "True" ; 
  } 
  return "False" ; 
}

int main(){
  struct Names test = {&isEqual , "Ayub"} ; 
  printf("%s\n" , test.cb("Hello")); 
  return EXIT_SUCCESS ; 
}

```
___
Tags : #programming #c #language 