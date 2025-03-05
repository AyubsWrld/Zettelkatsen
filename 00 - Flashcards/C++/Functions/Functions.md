___
Tags: #cpp #progarmming 
___
What is a function Prototype? ;; The functions identifier without its implementation ( The return type , name of the function , parameters ) 

What is a forward declaration? ;; A forward declaration is the process of telling the compiler about the existence of a certain identifier and providing its implementation later . 

How do we declare a forward definition for functions? ;; Through giving the compiler the functions prototype beforehand .

What does declaration do ? ;; Tells the compiler about an identifier and its associated type information . 

What is an example of a declaration? ;; void foo() , int x ( Variable definition )  

What does a definition do ? ;; Implements a function or instantiates a variable , Definitions are also declarations . 

What is an Example of a definition ? ;; void foo(){ do something } int x ( Variable definition is also declaration ) 

What is initialization ? ;; Provides an initial value for a defined object . 

What is an example of initialization ? ;; int x { 2 } // x is initialized to value 2 . 

What is Part 1 of the One Definition Rule (ODR) and what happens if it's violated? ;; Part 1 of ODR states that within a file, each function, variable, type, or template in a given scope can only have one definition.  **Violation Consequence:** Violating this part will cause the compiler to issue a redefinition error.

What is Part 2 of the One Definition Rule (ODR) and what happens if it's violated? ;; Part 2 of ODR states that within a program, each function or variable in a given scope can only have one definition across the entire program.   **Violation Consequence:** Violating this part will cause the linker to issue a redefinition error.

What is Part 3 of the One Definition Rule (ODR) and what happens if it's violated?;; Part 3 of ODR allows types, templates, inline functions, and inline variables to have duplicate definitions across different files, as long as each definition is identical.  **Violation Consequence:** Violating this part can lead to undefined behavior.

Does the compiler have any memory of the contents of separate files ? ;; No , the compiler compiles each code file individually (and then forgets what it has seen). For example each code file that uses `std::cout` or `std::cin` needs to `#include <iostream>`.

What happens if the compiler has seen neither a forward declaration nor a definition for an identifier in the file being compiled? ;; If the compiler has seen neither a forward declaration nor a definition for the identifier, it will issue an error at the point where the identifier is used.

What happens if a definition for an identifier exists in the same file? ;; If a definition exists in the same file, the compiler will connect the use of the identifier to its definition.

What happens if a definition for an identifier exists in a different file and is visible to the linker? ;; If a definition exists in a different file and is visible to the linker, the linker will connect the use of the identifier to its definition.

What happens if the linker cannot find a definition for an identifier? ;; If the linker cannot find a definition for the identifier, it will issue an error indicating that it couldn’t find a definition.

What is the design goal of C++ regarding source file compilation and the order in which files are compiled?;;C++ is designed so that each source file can be compiled independently, with no knowledge of what is in other files, meaning the order in which files are compiled should not be relevant. 