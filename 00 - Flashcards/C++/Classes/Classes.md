___
Tags: #cpp #programming
___

What is the Class Invariant problem ? ;; When our compound type is in an semantically invalid state which would cause undefined behavior.
<!--SR:!2025-05-27,3,250-->

Why are member functions defined within the body of the class implicitly inlined ? ;; To avoid breaking the one definition rule.
<!--SR:!2025-05-26,1,210-->

What should we think about with every class we write ? ;; Are there any state our object could be in that would place our object into a semantically incorrect state.
<!--SR:!2025-05-27,3,250-->


What is the difference between structs and classes ? ;; data/function members and implicitly public with structs and implicitly private with classes. 

What should getters return ? ;; They should return by value or by const l-value reference. 


What's wrong with this code ![[Pasted image 20250522224900.png]]? ;; UB, Ref is left dangling after the r-value expression is resolved.
<!--SR:!2025-05-27,3,250-->

Why should we refrain from returning non-const references to private members? ;; Because you can directly change the value of the returned reference without having to deal with the access control system.
<!--SR:!2025-05-27,3,250-->

True or false: Const member functions can’t return non-const references to data members ? ;; True, intuitively this makes sense because const member functions cannot change the state of the object so it would make sense that there is a mechanism which stops them from returning something which may alter the state of the object. 

Which access layer composes a classes interface , public or private ? ;; Public. A classes "interface" is usually called it's public interface.
<!--SR:!2025-05-26,1,227-->

Why shouldn't we utilize the private keyword with respect to structs ? ;; Structs do not and should not be utilized for implementing data hiding as that would defeat the purpose of their use as aggregates ( You usually want to use all the data you defined ).
<!--SR:!2025-05-27,3,250-->

What are some benefits of data hiding ? ;; Helps us manage invariants better, also we can remove the concern of having to understand the implementation. We simply concern ourselves with manipulating the interface. It also becomes quite easy to change the implementation of some interface without having to change the interface.
<!--SR:!2025-05-26,1,227-->

If we want good class design we should ? ;; Think about where the class invariants might occur and move all those places into private access layer.
<!--SR:!2025-05-26,1,227-->


True or False : Constructors create objects ? ;; No, the compiler allocates the memory needed for the class, the constructor simply initializes the memory with some value .
<!--SR:!2025-05-27,3,250-->

Does const effect an object in construction ? ;; No, If I have a const class I can still call its constructor to initialize its values.
<!--SR:!2025-05-26,1,227-->

Can the constructor ever be marked as being const ? ;; No, This is because the constructor should be able to initialize portions of the class itself. 

In what order are the members of a class initialized ? ;; In the order they are defined.
<!--SR:!2025-05-27,3,250-->


What is wrong with the following code snippet ![[Pasted image 20250523141521.png]]? ;; This results in UB, we try to initialize m_x with the value of m_y which isn't initialized until m_x is. It follows the way the it is defined.
<!--SR:!2025-05-27,3,250-->

When a member initializer list has finished executing, the object is considered what ? Initialized.

When the function body of the constructor has been executed, the object is considered what ? Constructed. Constness ensues after this. 


True or false: Suppose `foo` takes in class `Foo` as a parameter. Based off this call expression, the argument passed into `Foo` is an l-value: `foo( { 1 , 2 } )` ( Assume `Foos` constructor takes two integers ). ;; False, the argument passed to `foo` is an anonymous object and is an r-value whose lifetime is equivalent to the call site of foo.
<!--SR:!2025-05-27,3,250-->


What is a narrowing conversion ? ;; A conversion wherein the size of the type of target ( return value ) is less than the size of  type of the object we are casting from.
<!--SR:!2025-05-27,2,247-->

Give an example of a narrowing conversion ;; double to int ( 8 bytes to 4 ). Depends on implementation of course.
<!--SR:!2025-05-26,1,227-->

When should we prefer `static_cast` ? ;; When we want to create a temporary object and need to perform a narrowing conversion. We want to make it really obvious that we're converting to a type that will result in some different behavior ( e.g a `char` to an `int` ). We want to use direct-initialization for some reason (e.g. to avoid list constructors taking precedence).

What is the copy constructor ? ;; A **copy constructor** is a constructor that is used to initialize an object with an existing object of the same type. After the copy constructor executes, the newly created object should be a copy of the object passed in as the initializer.
<!--SR:!2025-05-26,1,227-->

True or false: Similar to a default constructor, the compiler generates a default copy constructor for every class object we declare. ;; True. 


What mechanism does copy construction utilize to initialize member variables ? ;; It utilizes memberwise initialization.
<!--SR:!2025-05-27,3,250-->

How can we define our own copy constructor? ;; `<Classname>( const <Classname>& x)`
<!--SR:!2025-05-27,3,250-->


What Constructor is called when an object is passed in by value ? ;; The copy constructor.
<!--SR:!2025-05-27,3,250-->

What constructor is used to create temporary objects ? ;; The copy constructor.
<!--SR:!2025-05-27,3,250-->

True or False: we can explicitly request the compiler to generate a copy constructor ourselves ( if so how ) ? ;; True , we can utilize the  = default keyword to do this.
<!--SR:!2025-05-26,1,230-->


How can we make our objects Non-copy constructible ? ;; Through deleting the copy constructor.
<!--SR:!2025-05-27,3,250-->

What is the rule of three ? ;;  If a user defined object needs a user defined default constructor, a copy constructor, or copy assignment operator, then it requires all three.
<!--SR:!2025-05-26,1,210-->

The parameter for a copy constructor must be a (const) reference. Why aren’t we allowed to use pass by value? ;; If the copy constructor used pass by value, the copy constructor would need to call itself to copy the initializer argument into the copy constructor parameter. But that call to the copy constructor would also be pass by value, so the copy constructor would be invoked again to copy the argument into the function parameter. This would lead to an infinite chain of calls to the copy constructor.
<!--SR:!2025-05-26,1,210-->

True or False: Any call to a function passing an object by value calls the copy constructor ? ;; True.
<!--SR:!2025-05-27,3,250-->

What are all the types of initializations used here ?![[Pasted image 20250523192123.png]];; default initialization, copy initialization, direct initialization, direct list initialization, copy list initialization, value initialization.
<!--SR:!2025-05-26,1,210-->


What is the difference between a non-explicit constructor list initializer ? ;; 

What is copy elision ? ;; Compiler optimization wherein the compiler removes unnecessary calls to the copy constructor.
<!--SR:!2025-05-27,3,250-->

What is meant by a constructor has been **elided** ? ;; The compiler optimized away a call to the constructor.
<!--SR:!2025-05-27,3,250-->

How many calls to the copy constructor are there in this snippet of code ![[Pasted image 20250523193810.png]]? ;; 4 .
<!--SR:!2025-05-26,1,227-->



Suppose the following: `Foo` has a constructor `Foo(int)`, there exists a function `printfoo( Foo f)`, is `foo(5)` a valid call ? If so, how ? ;; It is valid, the compiler looks for a function implicitly finds the `Foo(int)` constructor, creates a temporary `foo` object and initializes it with the value 5. This works even if the copy constructor is deleted. 


How many implicit conversions can be made ? ;; Only one. 


Does this code compile, if not why not ![[Pasted image 20250524130157.png]]? ;; This doesn't compile, we are trying to have the compiler conduct two implicit conversions for us which is now allowed. The first being the C-style string literal to std::string and the second being converting the call printEmployee(Employee e) to printEmployee( std::string ). 


What is the purpose of the `explicit` keyword with respect to constructors ? ;; Removes the ability for the constructor to act as a converting constructor.
<!--SR:!2025-05-27,2,247-->

What are the two consequences of utilizing the `explicit` keyword ? ;; An explicit constructor cannot be used to do copy initialization or copy list initialization. An explicit constructor cannot do implicit conversions since this uses copy initialization or copy list initialization. 


Suppose `Dollars(int)` is marked as explicit which of the following calls are valid ? ![[Pasted image 20250524132258.png]] ;; Valid, Valid , Compile Error, Valid , Valid.
<!--SR:!2025-05-26,1,227-->


What is best practice for `explicit` constructors ? ;; Copy and move constructors should not be made `explicit`. A constructor that takes a single argument should be made explicit
<!--SR:!2025-05-27,2,247-->
( Unless the conversion is performant ). A constructor that takes multiple arguments should not be made explicit. 


What is a literal type ? ;; A literal and a literal type are distinct (but related) things. A literal is a constexpr value that is inserted into the source code. A literal type is a type that can be used as the type of a constexpr value. A literal always has a literal type. However, a value or object with a literal type need not be a literal.
<!--SR:!2025-05-26,1,227-->

What is another difference between classes and structs ? ;; Aggregates can be constexpr by default, classes must be explicitly made constexpr.
<!--SR:!2025-05-26,1,227-->


True or false ? If you want your class to be able to be evaluated at compile-time, make your member functions and constructor constexpr. ;;
<!--SR:!2025-05-27,2,247-->

What is wrong with this code ![[Pasted image 20250524133858.png]]?;; Pair is not a literal type and is therefore not constexpr.
<!--SR:!2025-05-26,1,227-->


What is Procedural Programming ? ;; The process of creating "procedures" ( functions ) that implement our program logic. We pass data objects to these functions those functions perform operations on the data and then potentially return a result to be used by the caller. 


What is Object oriented programming ? ;; With **Object-oriented programming** (often abbreviated as OOP), the focus is on creating program-defined data types that contain both properties and a set of well-defined behaviors.


What is an access specifier ? ;; `public` `private`. 

What is the as-if rule ? ;; The compiler can modify the program however it likes in order to produce optimized code so long as the modification does not alter the programs observable behavior.
<!--SR:!2025-05-26,1,227-->


Give me the for this ![[Pasted image 20250524140044.png]];;![[Pasted image 20250524140019.png]]
<!--SR:!2025-05-27,2,247-->

How do we name destructors ? ;; Through a tilde followed by the name of the class. ~ClassName.
<!--SR:!2025-05-26,1,227-->


How many destructors is a class allowed to have ? ;; One and only one destructor. 


True or false: A destructor is allowed to have parameters ? ;; false. 

At what point is an object considered destroyed ? ;; When the objects destructor has finished executing.
<!--SR:!2025-05-27,2,247-->

name an issue that might be present when calling std::exit() ? ;; The program stops at the point the exit is executed. If this occurs before destruction logic can execute this might be bad ( especially if you rely on your destructor to do execute some clean up logic which is absolutely needed ).
<!--SR:!2025-05-26,1,227-->


What is an injected class name in the context of template classes? ;; An injected class name serves as a shorthand for the templated classname ( we don't have to `Classname<T>` in the constructor we simply just write `Classname` ).
<!--SR:!2025-05-26,1,227-->


True or False: Static members are shared by all objects of the same class ? ;; True.
<!--SR:!2025-05-26,1,227-->


What is the output of the following code snippet , why ? ![[Pasted image 20250524143709.png]];; 2 , 2. This static member s_value is shared between objects of the same type. Changes somewhere indicate changes elsewhere.
<!--SR:!2025-05-27,2,247-->

What are static member variables ? ;; Static members are global variables that live inside the scope region of the class.
<!--SR:!2025-05-27,2,247-->

True or False: static member is subject to access control system? ;; False, a static member is not subject to access control.
<!--SR:!2025-05-26,1,227-->

True or False: When an object which houses a static member is destroyed, the static member is destroyed as well ? ;; False, the static member exists throughout the lifetime of the entire program.
<!--SR:!2025-05-28,3,267-->

Where should we define our static members ? ;; In the .cpp implementation of our class. 

How can we initialize static member variables inside the classes definition ? ;; We can inline them so that they are expanded inline ( multiple definitions ).
<!--SR:!2025-05-26,1,227-->

What is best practice for Static Member Variables ? ;; Make your static members `inline` or `constexpr` so they can be initialized inside the class definition.

What is a class with all static members called ? ;; A monostate.
<!--SR:!2025-05-27,2,247-->

True or False: Static member variables exist before any instance of an owning object are instantiated. ;; True. 


How do we define and initialize static member variables ? ;; 