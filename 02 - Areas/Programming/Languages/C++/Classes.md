## Constructor
---
### Converting constructors and the *explicit* keyword
- *Implicit type conversion* occurs with more than just [[Datatypes]] , we can observe *implicit type conversion* with classes as well . take for example this code snippet
```cpp
#include <iostream>

class Dollars
{
private:
    int m_dollars{};

public:
    explicit Dollars(int d) // now explicit
        : m_dollars{ d }
    {
    }

    int getDollars() const { return m_dollars; }
};

void print(Dollars d)
{
    std::cout << "$" << d.getDollars();
}

int main()
{
    print(5); // compilation error because Dollars(int) is explicit

    return 0;
}
```
In this case if the compiler does not see the *explicit* ,  5 can be implicitly converted  to fit the function call so the compiler does as such (**Converting Constructor**) . However prefacing the constructor with *explicit* allows us to stop this from occurring  . 

-  ===Attempting to return values which are not of type of the class you wish to return when an explicit constructor exists will throw and exception always== 

### Best practices for use of `explicit` 
The following **should not** be made explicit:

- Copy (and move) constructors (as these do not perform conversions).

The following **are typically not** made explicit:

- Default constructors with no parameters (as these are only used to convert `{}` to a default object, not something we typically need to restrict).
- Constructors that only accept multiple arguments (as these are typically not a candidate for conversions anyway).

However, if you prefer, the above can be marked as explicit to prevent implicit conversions with empty and multiple-argument lists.

The following **should usually** be made explicit:

- Constructors that take a single argument.

There are some occasions when it does make sense to make a single-argument constructor non-explicit. This can be useful when all of the following are true:

- The constructed object is semantically equivalent to the argument value.
- The conversion is performant.
### Constexpr aggregates and classes
```cpp
#include <iostream>

struct Pair // Pair is an aggregate
{
    int m_x {};
    int m_y {};

    constexpr int greater() const
    {
        return (m_x > m_y  ? m_x : m_y);
    }
};

int main()
{
    constexpr Pair p { 5, 6 };       // now constexpr
    std::cout << p.greater();        // p.greater() evaluates at runtime or compile-time

    constexpr int g { p.greater() }; // p.greater() must evaluate at compile-time
    std::cout << g;

    return 0;
}
```
