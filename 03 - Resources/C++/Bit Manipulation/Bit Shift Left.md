> [!note] Purpose
>  ###### `<<=` : Shifts the bit n spots to the left.

> [!example] 

```cpp
#include <bitset> 
#include <iostream> 

int main(){
std::bitset<8> bin = 0b0000'0001 ; // Bitwise representation of 1
std::cout << bin << std::endl  ; 
bin = bin <<= 1 ; 
std::cout << bin << std::endl  ;  // becomes 0b0000'0010, bitwise 2 
return 0 ; 
}
```

___
Tags : #progarmming #cpp 