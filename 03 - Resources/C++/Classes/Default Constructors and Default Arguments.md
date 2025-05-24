##### Value Initialization vs. Default initialization for class types.
____
both `Foo foo{}` and `Foo foo` call the default constructor for the class. 

##### Constructors with default arguments. 
___
```cpp
class Foo{
	int m_x ; 
	int m_y ; 
public:
	Foo( int x=0 , int y=0 ) // Default constructor 
	: m_x{x}
	, m_y{y} 
	{}
}
```

`Foo foo{}` -> `foo{ 0, 0}`    ,  `Foo foo{ 1 , 2 }` -> `foo{1,2}`

However both call the default constructor. 

##### overloaded constructors.
___
Multiple default constructors can exist and it is usually the case that the compiler generates a default constructor if there isn't one. 

##### Explicit Default constructor. 
___
We can utilize the `default` keyword to explicitly tell the compiler which of our defined constructors should act as the default. This constructor is called an *explicitly defaulted default constructor*. 

```cpp
#include <iostream>

class Foo
{
private:
    int m_x {};
    int m_y {};

public:
    Foo() = default; // generates an explicitly defaulted default constructor

    Foo(int x, int y)
        : m_x { x }, m_y { y }
    {
        std::cout << "Foo(" << m_x << ", " << m_y << ") constructed\n";
    }
};

int main()
{
    Foo foo{}; // calls Foo() default constructor

    return 0;
}
```

In the above example, since we have a user-declared constructor (`Foo(int, int)`), an implicit default constructor would not normally be generated. However, because we’ve told the compiler to generate such a constructor, it will. This constructor will subsequently be used by our instantiation of `foo{}`.

##### Explicitly defaulted default constructor vs empty user-defined constructor.
___
Two cases when they are different. 

- Whenever a user defined default constructor which is not an explicitly defaulted default constructor is called using value initialization, the values are not default initialized. 

##### Delegating Constructors
___
Constructors are allowed to delegate initialization to another constructor from the same class type. This process is called *Constructor Chaining*.

```cpp
#include <iostream>
#include <string>
#include <string_view>

class Employee
{
private:
    std::string m_name { "???" };
    int m_id { 0 };

public:
    Employee(std::string_view name)
        : Employee{ name, 0 } // delegate initialization to Employee(std::string_view, int) constructor
    {
    }

    Employee(std::string_view name, int id)
        : m_name{ name }, m_id { id } // actually initializes the members
    {
        std::cout << "Employee " << m_name << " created\n";
    }

};

int main()
{
    Employee e1{ "James" };
    Employee e2{ "Dave", 42 };
}
```


___
Tags: #cpp #programming