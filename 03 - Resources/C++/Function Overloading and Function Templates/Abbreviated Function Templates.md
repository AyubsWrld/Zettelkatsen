Introduced into `C++20` , when a functions signature has the `auto` keyword in both its return value and all of its arguments the compiler converts it into a template with each variable being assigned a different type. 

```cpp 
auto min( auto x , auto y )
{
	return x > y ? y : x ; 
}

// becomes 
template < typename T , typename U > 
auto min( T x , U y ) 
{
	return x > y ? y : x ; 
}
```
___
Tags :  #cppfunctions 