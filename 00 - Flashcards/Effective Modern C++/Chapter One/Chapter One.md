
___
Tags: #cpp #idioms
___

What is template type deduction, and when does it occur? ;; To be filled  

What are the three categories of `ParamType` in a template function and how do they affect deduction? ;; To be filled  

How and what does the compiler use to deduce the two types: ![[Pasted image 20250527111843.png]] ;; the type of expr is used to deduce the type of `paramtype` and the type of `T`.
<!--SR:!2025-06-01,4,270-->

Given: `f(ParamType param)` , how is `T` deduced when `Paramtype` is a reference or pointer but not a universal pointer ? ;; References are ignored and expr is pattern-matched against `ParamType` to determine `T`. 

What is the the type of T and `ParamType` if `f(x)` where `int x = 27;`? ![[Pasted image 20250527112407.png]];; `T` is a `int` , `ParamType` is a `int&` .
<!--SR:!2025-05-31,3,250-->

What is the the type of T if `f(x)` where `const int x = 27;`? ![[Pasted image 20250527112407.png]];; `T` is a `const int` , `ParamType` is a `const int&` .
<!--SR:!2025-05-31,3,250-->

What is the the type of T if `f(x)` where `const int& x = 27;`? ![[Pasted image 20250527112407.png]];; `T` is `const int` , `ParamType` is a `const int&` .


How are `T` and `ParamType` deduced when passing by a Universal Reference and `expr` is passed in as an l-value ? ;; Both `T` and `ParamTypes` are l-value references.
<!--SR:!2025-06-01,4,270-->

How are `T` deduced when `ParamType` a Universal Reference and `expr` is passed in as an r-value ? ;; `T` becomes the type of `expr` and `ParamType` becomes an r-value reference. 

True or False: When universal references are in use, type deduction distinguishes between lvalue arguments and rvalue arguments. That never happens for non-universal references.;; True. 

What is the type of `T` when ParamType is Neither a Pointer nor a Reference ( by value ) ? ;; both `T` and `ParamType` are set to the trivial ( decayed ) value of `expr`
<!--SR:!2025-05-31,3,250-->

Based on the following code snippet what is the value of `T` ![[Pasted image 20250527115639.png]] ;; Both `T` and `ParamType` are `int*`.
<!--SR:!2025-05-31,3,250-->

Based on the following code snippet what is the value of `T`? 
![[Pasted image 20250527115807.png]] ;; Both `T` and `ParamType` are `int*`. 


Based on the following code snippet what are the type values of `T` and `ParamType`? Is the pointers `constness` preserved? Why ?![[Pasted image 20250527120401.png]];; `T` is char and `ParamType` is `const char*` , No the `constness` of the pointer is not preserved because the bits making up the `ptr` are copied and can be modified ( the pointer can now be reseated and nulled ) whereas the value of the object which the pointer points to cannot be.
<!--SR:!2025-05-29,1,230-->

True or False: The type of a Parameter and the type of the value being passed in are distinct and can differ. ;; True, in fact this is how type casting works in some cases. 

What is the type value of a parameter who was passed in as an array by value ? ;; A pointer ( the type decays into a pointer to the type housed by the array ).
<!--SR:!2025-05-31,3,250-->

Suppose `name` is a character array, what is the type of `T` and and `ParamType` : ![[Pasted image 20250527121702.png]];; The type of the array is preserved.
<!--SR:!2025-05-31,3,250-->

What is the output of this code ? ![[Pasted image 20250527122356.png]];; sizeof(words)
<!--SR:!2025-05-29,1,230-->

How does this code work? ![[Pasted image 20250527122527.png]];; When an array is passed by reference it does not decay into a pointer, thus its type is passed in simply as is. So if we pass in a type like `const char arr[5]`, array type is preserved therefore we get `const char (&)[5]`. N is captured as the size of the type within the argument. 

What is the type of `const char somearr[5]` ? ;; `const char[5]`


What two types decay into pointers when passed into functions ? ;; Arrays and pointers.
<!--SR:!2025-05-31,3,250-->


What is array-to-pointer decay ? ;; When an array past in by value degenerates to a pointer.
<!--SR:!2025-05-31,3,250-->


What is the type of `x` : `auto x = { 27 }` ? ;; Initializer list set to `{ 27 }`.
<!--SR:!2025-06-01,4,270-->


Can we deduce type of a brace initialized within a template ? ;; No.
<!--SR:!2025-05-31,3,250-->

What is the difference between auto type deduction and template type deduction ? Auto type deduction is the same as template type deduction, but auto type deduction assumes that braced initialization represents std::initializer_list whereas template type deduction doesn't. 

What does auto return type within a function or lambda parameter imply ? ;; Template type deduction, not auto type deduction 

Will this code compile ? why or why not ? ![[Pasted image 20250527132322.png]];; auto within lambda's conform to template type deduction not auto type deduction.
<!--SR:!2025-05-31,3,250-->

What advantages does a trailing return type yield ? ;; A trailing return type has the advantage that the function's parameters can be used in the specification of the return type. 

Whats wrong with the following code snippet : ![[Pasted image 20250527140638.png]];; auto within the return statement returns conforms to template type deduction ( `auto` casts away reference and just returns by value ), we want a reference to the user so we must supplement `auto` with `auto&`, this retains reference.
<!--SR:!2025-06-01,4,270-->


