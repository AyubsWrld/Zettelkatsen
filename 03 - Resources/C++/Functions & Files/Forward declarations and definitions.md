Compiler compiles the contents of a source file sequentially
-> this implies that if we want to utilize a function it must be forward declared or already declared . We usually get an Identifier error when we try to call a function which we haven't declared yet . 

### Why do we forward declare ? 
in Larger programs it can be tedious figuring out the order in which functions where declared and if we are able to call them in that part of the code . Also there might be a time where we have two functions which call each other ( Circular Dependencies ) . 


### Solution : Forward Declaration . 

Allows us to tell the compiler the existence of an identifier before we actually define the identifier itself . 


### Declaration vs Definition 

A **declaration** is telling the compiler the existence of an identifier. 

A **definition** is a declaration that actually implements (for functions and types) or instantiates (for variables) the identifier.

| Term                 | Technical Meaning                                                                    | Examples                                                                                                                                         |
| -------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Declaration**      | Tells compiler about an identifier and its associated type information.              | `void foo(); // function forward declaration (no body)`<br>`void goo() {}; // function definition (has body)`<br>`int x; // variable definition` |
| **Definition**       | Implements a function or instantiates a variable. Definitions are also declarations. | `void foo() { } // function definition (has body)`<br>`int x; // variable definition`                                                            |
| **Pure declaration** | A declaration that isn’t a definition.                                               | `void foo(); // function forward declaration (no body)`                                                                                          |
| **Initialization**   | Provides an initial value for a defined object.                                      | `int x { 2 }; // x is initialized to value 2`                                                                                                    |

### One Definition Rule ( ODR ) 
- **Within a file**: Each function, variable, type, or template in a given scope can only have one definition. Definitions in different scopes (e.g., local variables in different functions or functions in different namespaces) don't violate this rule.
    
- **Within a program**: Each function or variable in a given scope can only have one definition across the entire program. Definitions not visible to the linker (such as those with internal linkage) are excluded from this rule.
    
- **Types, templates, inline functions, and inline variables**: These can have duplicate definitions across different files, as long as each definition is identical.

Violating part 1 of the ODR will cause the compiler to issue a redefinition error. Violating ODR part 2 will cause the linker to issue a redefinition error. Violating ODR part 3 will cause undefined behavior.