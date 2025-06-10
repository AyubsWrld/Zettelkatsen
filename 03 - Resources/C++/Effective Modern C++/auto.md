#### Prefer auto to explicit type declarations.
___
- The `auto` keyword makes initialization of objects with verbose types easy. 
- We can utilize auto to capture types only known by the compiler like the values of closures.
- `std::function` is a templated class object which stores a reference to any callable object ( lambda or function for example ). 
- An auto declared closure has the same type as the closure, and therefore uses up as much memory as the closure itself. On the other hand an `std::function` has a fixed size which may not be adequate enough to store the closure itself. At some point heap allocation may occur. 
- `std::functions` verbosity and potential heap allocation is what makes it a lot less desirable to use. 
- `auto` can directly hold closures. 
- auto variables must be initialized, are generally immune to type mismatches that can lead to portability or efficiency problems, can ease the process of refactoring, and typically require less typing than variables with explicitly specified types.
#### Use the explicitly typed initializer idiom when auto deduces undesired types.
___
- “Invisible” proxy types can cause auto to deduce the “wrong” type for an ini tializing expression. 
- The explicitly typed initializer idiom forces auto to deduce the type you want it to have.



#### Questions
___
- **What is `std::function`.**
- **What is the difference between `std::function` and `auto` for storing closures?**. 
- **What happens to `std::function` when it runs out of space**.
- **Why should we prefer `auto` over explicit type declarations**?
- **What are the advantages of using `auto`** 
____
Tags: #programming #cpp