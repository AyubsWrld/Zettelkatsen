We can instantiate a template function with multiple different types through defining multiple types in the `typename` declaration. 

```cpp

template < typename T , typename U > 
T min( T x , U y) 
{
	return x > y ? y : x ; 
}
```

> [!error]
> Although will compile there is chance that U is returned, and given that U is of different type than T it might be the case that U is implicitly cast to type T. 

We can solve this through the use of the `auto` keyword. 
```cpp
// Proned to semantic errors , becomes 

template < typename T , typename U > 
T min( T x , U y)  // type U might be returned 
{
	return x > y ? y : x ; 
}

// This 
template < typename T , typename U > 
auto min( T x , U y)  // type U might be returned 
{
	return x > y ? y : x ; 
}

```
___
Tags :  #cppfunctions 