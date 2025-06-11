___
Tags: #cpp #programming
___

What is a base specifier list ? ;; The base-specifier-list **specifies the type of the base class subobjects contained in an object of the derived class type**.

What is a mem-initializer list ? ;; The portion of the construction which initializes member variables. 

What does a template argument list do ? ;; Denotes the types of a template. `std::tuple<int,char,std::string>()` .

How are parameter packs denoted ? ;; Through the use of an ellipsis. 

What is the "pattern" with respect to parameter packs ? ;; The pattern is the unit of work which is applied to every individual object within the pack. 

Within this code snippet which is the pattern ![[Pasted image 20250524231420.png]]? ;; ( ( std::cout << c << " " << N << " " ) , ... ) 


Write a variadic template function that returns the size of the largest type in the list. Then modify the code to use your own function `getMax` to return the size of the of the value;; ![[Pasted image 20250525000502.png]]



