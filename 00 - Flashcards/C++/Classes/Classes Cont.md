___
Tags: #cpp #programming
___

If we have a user defined constructor, say of type `int ( int, int)`, will the compiler implicitly generate a default constructor ? ;; No, the user defined constructor would be considered the default. 

What is *Constructor Chaining* ? ;; The process of one constructor delegating initialization to another constructor belonging to the same class type. 

How is *Constructor Chaining Done* ? ;; Through calling the constructor in the member initialization list. 

True or false: A constructor which delegates initialization is not allowed to do initialization itself. ;; True. 

What is best practice when you have multiple constructors ? ;; If you have multiple constructors, consider whether you can use delegating constructors to reduce duplicate code.

Quiz : ![[Pasted image 20250523161231.png]] ;; Solved.


True or false: Expressions exist only in the lines they are utilized ? ;; True. 