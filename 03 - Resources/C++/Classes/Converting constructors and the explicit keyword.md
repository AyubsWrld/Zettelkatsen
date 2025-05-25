Similar to how some the compiler can implicitly conduct type conversions for us, such as making a call to `foo(int)` when we pass it a double ( narrowing conversion ). So too can this occur with the constructor of some object. 

```cpp
#include <iostream>

class Foo
{
private:
    int m_x{};
public:
    Foo(int x)
        : m_x{ x }
    {
    }

    int getX() const { return m_x; }
};

void printFoo(Foo f) // has a Foo parameter
{
    std::cout << f.getX();
}

int main()
{
    printFoo(5); // we're supplying an int argument

    return 0;
}
```

In this case a temporary object `Foo` is initialized with the value `5` and is then used to call `printFoo()`. This is because the compiler looks for matching function calls even within the bounds of objects. These are referred to as converting constructor. 

##### The `explicit` keyword
___
The explicit keyword tells the compiler that the constructor should not be used as a converting constructor. Making a constructor explicit has two notable consequences. 

- An explicit constructor cannot be used to do copy initialization or copy list initialization.
- An explicit constructor cannot be used to do implicit conversions (since this uses copy initialization or copy list initialization).

this goes for returning values as well. 

```cpp
#include <iostream>

class Foo
{
public:
    explicit Foo() // note: explicit (just for sake of example)
    {
    }

    explicit Foo(int x) // note: explicit
    {
    }
};

Foo getFoo()
{
    // explicit Foo() cases
    return Foo{ };   // ok
    return { };      // error: can't implicitly convert initializer list to Foo

    // explicit Foo(int) cases
    return 5;        // error: can't implicitly convert int to Foo
    return Foo{ 5 }; // ok
    return { 5 };    // error: can't implicitly convert initializer list to Foo
}

int main()
{
    return 0;
}
```

___
Tags: #cpp #programming