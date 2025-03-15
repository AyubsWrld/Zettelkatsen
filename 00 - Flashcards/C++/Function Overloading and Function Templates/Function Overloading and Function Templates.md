___
Tags: #cpp #programming
___

What is overload resolution ? ;; The process of the compiler selecting which definition is the best match for a given function call. 
<!--SR:!2025-03-17,3,250-->

How are overloaded functions differentiated ? ;; Number of parameters and type of parameters.
<!--SR:!2025-03-17,3,250-->

Is this valid ? if so why ![[Pasted image 20250314180300.png]];; Yes , overload resolution results in this being valid , the compiler can differentiate between these two functions because of the number of parameters.
<!--SR:!2025-03-17,3,250-->

Are these two functions differentiated ![[Pasted image 20250314180459.png]]? ;; No, even though the return types differ the compiler cannot differentiate one from the other.
<!--SR:!2025-03-15,1,230-->

What happens when there is an exact match with a function call and a given function ? ;; The functions call is assigned that definition. Numeric Promotion may occur here. 

What is Numeric Promotion ? ;; The conversion of a narrower type to a larger type. 

What happens if no exact match with between a given function and a function call are found ? ;; Numeric conversion will occur ( `char` to `double` )

How can you delete a function ? ;; Utilizing the `delete` keyword.  

What's the problem with deleting individual functions one by one ? ;; verbose , you can end up with a long list of delete statements just to combat overload resolution . 

How can we get around the verbosity of deleting multiple functions? ;; through the use of template functions ![[Pasted image 20250314192245.png]]

What are Default Arguments ?;; A default argument is a default value provided for a function parameter. 


When are default parameters handled by the compiler ?;; at the call site ( callDefault(3) => callDefault(3 , 4)) assuming 4 was a default parameter. 

When is it a good idea to use default paramters ? ;; when we want to allow the caller to be able to be allowed to specify whether they want to pass in parameters or not. or we have a default value just in case . ( void openLogFile( std::string filename="default.log")).

In what order must we emit default values ? ;; From left to right . 

True or false ? If a parameter is given a default argument, all subsequent parameters (to the right) must also be given default arguments. ( Will void print(int x=10, int y) work? );; true , the snippet wont work either. 

True or False ? Default arguments can be redeclared, they may be declared before use ;; false

Will this work , if not why and how can we fix it ? ![[Pasted image 20250314193145.png]];; No , redeclaration of default arguments . If we want to do this we must leave the forward declaration without default arguments and then include the default arguments when we are defining the function. 