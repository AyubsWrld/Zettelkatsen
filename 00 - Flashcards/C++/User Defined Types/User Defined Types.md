___
Tags: #cpp #programming
___
True or false? a program-defined types must be fully implemented before it can be used, a forward declaration will not suffice. ;; True.

When could the Specifying the base type of an enumeration cause undefined behavior;; May cause how the compiler treats the value for example if we set it to int8_t it gets treated as a char as opposed to an integer.  

Who chooses the implementation type of an enumeration if it is not specified ? ;; The compiler. 

How can you determine what can safely be static_casted within an enumeration? ;; Through checking the bounds of enumerated type. With enumerators that have values 2, 9, and 12, these enumerators could minimally fit in an unsigned 4-bit integral type with range 0 to 15. Therefore, it is only safe to static_cast integral values 0 through 15 to this enumerated type.

True or false. Enumerators can be Given an integer value ? ;; True.

True or false. Enumerators can be given no explicit value? ;; Enumerators not explicitly assigned a value will be implicitly assigned the integer value of the previous enumerator + 1. If there is no previous enumerator, the enumerator will assume value 0.

True or false. Enumerators can be given a floating point value ? ;; False.

True or false. Enumerators can be given a non-unique value ? ;; True. 

True or false. Enumerators can be - Given the value of a prior enumerator (e.g. magenta = red) ;; True. Enumerators need not be unique. Since enumerators implicitly convert to integers, and integers can be given to enumerators, enumerators can be initialized with other enumerators (though there is typically little reason to do so!).

True or false. Enumerators can be - Given a non-constexpr value ;; False. Since enumerators are constexpr, their values must also be constexpr.

What are the steps of Operator Overloading? ;; Basic operator overloading is fairly straightforward: Define a function using the name of the operator as the function’s name, Add a parameter of the appropriate type for each operand (in left-to-right order). One of these parameters must be a user-defined type (a class type or an enumerated type), otherwise the compiler will error, Set the return type to whatever type makes sense, Use a return statement to return the result of the operation.

How does operator overloading work ?;; When the compiler comes across the use of an operator within an expression and one or more of the operands is a user-defined type, the compiler checks to see if there is an overloaded function that it can use to resolve that call. If there is it executes the functions and utilizes the return value of said function. 