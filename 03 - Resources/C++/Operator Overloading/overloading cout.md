`std::cout` is of type std::ostream, takes left right hand operand and resolves the function call returning a reference to `std::cout` for further use. 

```cpp
#include <iostream>
#include <string.h>

namespace Items
{
  enum Weapon 
  {
    hands, // Default case
    sword, 
    staff,
    dagger,
    rapier,
    greatsword
  };
}

constexpr std::string_view enum_to_string( Items::Weapon weapon )
{
  switch (weapon) {
    case Items::sword: 
      return "Sword";

    case Items::staff: 
      return "Staff";

    case Items::dagger: 
      return "Dagger";

    case Items::rapier: 
      return "Rapier";

    case Items::greatsword: 
      return "Greatsword";
    default:    
      return "Hands";
  }
}


std::ostream& operator<<( std::ostream& cout, Items::Weapon weapon )
{
  cout << enum_to_string(weapon) ; 
  return cout;
}

int main (int argc, char *argv[]) 
{
  std::cout << Items::staff << std::endl ; 
  return 0;
}
```
___
Tags : #programming #cpp