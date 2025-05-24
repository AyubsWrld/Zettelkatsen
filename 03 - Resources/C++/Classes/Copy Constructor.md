```cpp
#include <iostream>

class Fraction
{
private:
    int m_numerator{ 0 };
    int m_denominator{ 1 };

public:
    // Default constructor
    Fraction(int numerator=0, int denominator=1)
        : m_numerator{numerator}, m_denominator{denominator}
    {
    }

    void print() const
    {
        std::cout << "Fraction(" << m_numerator << ", " << m_denominator << ")\n";
    }
};

int main()
{
    Fraction f { 5, 3 };  // Calls Fraction(int, int) constructor
    Fraction fCopy { f }; // What constructor is used here?

    f.print();
    fCopy.print();

    return 0;
}
```

This compiles and calls the copy constructor. A **copy constructor** is a constructor that is used to initialize an object with an existing object of the same type. After the copy constructor executes, the newly created object should be a copy of the object passed in as the initializer.

- We can define our own utilizing the `classname( const classname& x)` signature. 
- Copy constructors should not have any side effects beyond copying. 
- When an object is passed in by value it makes a call to the copy constructor 
- We can also explicitly request the compiler to generate a default copy constructor similar to how we can request a default constructor. 
- We can also make our objects `non-copyable` through deleting the copy constructor using the `delete` keyword. 

##### Rule of Three
___
If a user defined object needs a user defined default constructor, a copy constructor, or copy assignment operator, then it requires all three.

___
Tags: #cpp #programming