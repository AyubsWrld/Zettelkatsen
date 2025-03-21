an expression is “a combination of literals, variables, operators, and function calls that can be executed to produce a singular value”.

All Expressions have to properties, a type and value category. 
- The *type* is equivalent to the type expression resolves to 
- The *value* category of an expression determines whether a value resolves to a function , a value , or an object of some kind. 

- Lvalue expressions are those that evaluate to functions or identifiable objects (including variables) that persist beyond the end of the expression.
- Rvalue expressions are those that evaluate to values, including literals and temporary objects that do not persist beyond the end of the expression.

```cpp
#include <iostream>
#include <string>

// T& is an lvalue reference, so this overload will be preferred for lvalues
template <typename T>
constexpr bool is_lvalue(T&)
{
    return true;
}

// T&& is an rvalue reference, so this overload will be preferred for rvalues
template <typename T>
constexpr bool is_lvalue(T&&)
{
    return false;
}

// A helper macro (#expr prints whatever is passed in for expr as text)
#define PRINTVCAT(expr) { std::cout << #expr << " is an " << (is_lvalue(expr) ? "lvalue\n" : "rvalue\n"); }

int getint() { return 5; }

int main()
{
    PRINTVCAT(5);        // rvalue
    PRINTVCAT(getint()); // rvalue
    int x { 5 };
    PRINTVCAT(x);        // lvalue
    PRINTVCAT(std::string {"Hello"}); // rvalue
    PRINTVCAT("Hello");  // lvalue
    PRINTVCAT(++x);      // lvalue
    PRINTVCAT(x++);      // rvalue
}
```

This method relies on two overloaded functions: one with an lvalue refrence parameter and one with an rvalue reference parameter. The lvalue reference version will be preferred for lvalue arguments, and the rvalue reference version will be preferred for rvalue arguments. Thus we can determine whether the argument is an lvalue or rvalue based on which function gets selected.

So as you can see, whether `operator++` results in an lvalue or an rvalue depends on whether it is used as a prefix operator (which returns an lvalue) or a postfix operator (which returns an rvalue)!
___
Tags : #programming #cpp 