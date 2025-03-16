When a template function is called the compiler will be unable to resolve a direct match to the call and it will be implicitly converted into the template we have created. 

```cpp 
template <typename T> 
T getMax( T x , T y ) //Implicitly converted into this.
{
	return x > y ? x : y ; 
}


int main()
{
	int x = getMax<int>( 3 , 1 ) ;  // getMax<int>(int,int) not found
	return 0; 
}
```

This process of creating a function when a template function is called if referred to as template function instantiation. 


When we call `getMax<int>(int,int)` this specialization function is instantiated.

```cpp 
template<>
int max<int>( int x , int y )
{
	return x > y ? x : y ; 
}
```

A specialization function is only instantiated once per translation unit when it is called , after which any call made to it after is simply routed to the already instantiated function call.  

```cpp 
#include <iostream>

template <typename T>
T max(T x, T y) // function template for max(T, T)
{
    return (x < y) ? y : x;
}

int main()
{
    std::cout << max<int>(1, 2) << '\n';    // instantiates and calls function max<int>(int, int)
    std::cout << max<int>(4, 3) << '\n';    // calls already instantiated function max<int>(int, int)
    std::cout << max<double>(1, 2) << '\n'; // instantiates and calls function max<double>(double, double)

    return 0;
}
```

#### Deleting template functions 
____
Sometimes we may desire to remove some template specializations, we can do this through the use of the `delete` operator. 

```cpp 

template <typename T>
T print( T x )
{
	return x ;
}

template <>
const char* print( const char* x ) = delete ;  

int main()
{
	std::cout << print("Hello world")  << std::endl ; // compiler err
	return 0; 
}
```

#### Function templates and default arguments for non-template parameters

```cpp 
#include <iostream>

template <typename T>
void print(T val, int times=1)
{
    while (times--)
    {
        std::cout << val;
    }
}

int main()
{
    print(5);      // print 5 1 time
    print('a', 3); // print 'a' 3 times

    return 0;
}
```
___
Tags :  #cppfunctions 