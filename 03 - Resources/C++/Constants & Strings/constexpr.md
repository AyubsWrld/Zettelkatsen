Tells the compiler that this value or function must be evaluated at **compile time**, not runtime. Must be comprised of constexpr operands. We can think of it as a type-safe way of declaring macros. The compiler will replace any instance of the constexpr expression with the value it resolves to. 

For example we want to calculate $cos(\dfrac{FOV}{2})$ and we know that this expression is made up of constant literals that remain unchanging always. 
___
Tags : #programming #cpp 