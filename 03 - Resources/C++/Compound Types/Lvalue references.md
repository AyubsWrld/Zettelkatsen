An lvalue reference is a reference to an existing object which we can use to refer to or modify said object. 

### Lvalue references types
___
Similar to how the type of an object delineates what type of object it can hold , the type of an Lvalue reference determines what type it can reference (`int&` can only reference int). `int&` is referred to as the reference type whereas `int` is the type being referenced. 

#### Two types of Lvalue References 
___
An lvalue reference to a non-const is commonly just called an “lvalue reference”, but may also be referred to as an **lvalue reference to non-const** or a **non-const lvalue reference** (since it isn’t defined using the `const` keyword).
An lvalue reference to a const is commonly called either an **lvalue reference to const** or a **const lvalue reference**.

#### Reference initialization
___
Similar to constant values , lvalue references must be initialized. This process of initializing is referred to as binding. 

```cpp
int main()
{
    int& invalidRef;   // error: references must be initialized

    int x { 5 };
    int& ref { x }; // okay: reference to int is bound to int variable

    return 0;
}
```


#### References can’t be reseated (changed to refer to another object)
___
Once an lvalue reference is bound to an object it cannot be changed to reference a different variable. 

```cpp
#include <iostream>

int main()
{
    int x { 5 };
    int y { 6 };

    int& ref { x }; // ref is now an alias for x

    ref = y; // assigns 6 (the value of y) to x (the object being referenced by ref)
    // The above line does NOT change ref into a reference to variable y!

    std::cout << x << '\n'; // user is expecting this to print 5

    return 0;
}
```

Surprisingly this returns 6 as references resolve to their value when used within an expression. 

#### Reference scope and duration
___
References share the same scope and duration as the object they reference. 

#### References aren’t objects
___
Since reference types aren't objects ( And the compiler just goes around everywhere the reference object is used and replaces it with the object being referenced ) we cannot make a reference to a reference `int&&`. 

In the case you need a reference that is an object or a reference that can be reseated we must use `std::reference_wrapper` . 

___
Tags : #programming #cpp 