A **non-type template parameter** is a template parameter with a fixed type that serves as a placeholder for a `constexpr` value passed in as a template argument. 

A non-type template parameter can be any of the following types:
- An integral type
- An enumeration type
- `std::nullptr_t`
- A floating point type (since C++20)
- A pointer or reference to an object
- A pointer or reference to a function
- A pointer or reference to a member function
- A literal class type (since C++20)

```cpp 

template <int N> 
void print()
{
	std::cout << "Hello" <<  std::endl ; 
}
```
___
Tags :  #cppfunctions 
