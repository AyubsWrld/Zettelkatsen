Similar to how within regular function calls we can pass in [[r-values]] directly into the call site of the function. 

```cpp

void foo( int x )
{
	std::cout << x + 1 << std::endl ;  // Temporary object x created here.
}

int main()
{
	foo( 4 + 3 ) ;
	return 0
}
```

The same can be done with aggregates and classes. We create an anonymous object whose lifetime exists only during the duration of the call site of the function. 

```cpp
class Foo
{
	int m_x  ; 
	int m_y  ; 
public: 
	Foo( int x , int y ) 
	: m_x{x} 
	, m_y{y}
	{}

	void print_values()
	{
		std::cout << m_x  << " " << m_y << std::endl ; 
	}
}

void callPrint( Foo x )
{
	x.print_values() ;
}

int main()
{

	callPrint( Foo{ 1 , 2 } ) ; // Anonymous object created for the callsite. 
	callPrint( { 1 , 2 } ) ; // Anonymous object created for the callsite. 
	return 0
}
```

First, just as in the case of an `int`, when used in an expression, a temporary class object is an rvalue. Thus, such objects can only be used where rvalue expressions are accepted.

Second, temporary objects are created at the point of definition, and destroyed at the end of the full expression in which they are defined . A full expression is an expression that is not a subexpression.


##### `static_cast` vs explicit instantiation of a temporary object
___
Prefer `static_cast` when converting to a fundamental type, and a list-initialized temporary when converting to a class type.
___
Tags: #cpp #programming