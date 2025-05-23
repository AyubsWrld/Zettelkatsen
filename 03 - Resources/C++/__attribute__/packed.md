```cpp
#include <iostream>


struct __attribute__((packed)) Block_Packed
{ 
  int  x ;  //  4
  char y ; //   1 
};

struct Block_Unpacked
{ 
  int  x ;  //  4
  char y ; //   1 
};

int main()
{
  std::cout << sizeof( Block_Packed ) << "\n" ; 
  std::cout << sizeof( Block_Unpacked ) << "\n" ; 
  return 0; 
}



```
___
Tags : #programming #cpp 