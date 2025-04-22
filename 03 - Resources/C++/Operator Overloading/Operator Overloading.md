Basic operator overloading is fairly straightforward:

- Define a function using the name of the operator as the function’s name.
- Add a parameter of the appropriate type for each operand (in left-to-right order). One of these parameters must be a user-defined type (a class type or an enumerated type), otherwise the compiler will error.
- Set the return type to whatever type makes sense.
- Use a return statement to return the result of the operation.
___
Tags : #programming #cpp 