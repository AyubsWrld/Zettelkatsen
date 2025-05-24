___
Tags: #cpp #programming
___

What is the Class Invariant problem ? ;; When our compound type is in an semantically invalid state which would cause undefined behavior. 

Why are member functions defined within the body of the class implicitly inlined ? ;; To avoid breaking the one definition rule. 

What should we think about with every class we write ? ;; Are there any state our object could be in that would place our object into a semantically incorrect state. 


What is the difference between structs and classes ? ;; data/function members and implicitly public with structs and implicitly private with classes. 

What should getters return ? ;; They should return by value or by const l-value reference. 


What's wrong with this code ![[Pasted image 20250522224900.png]]? ;; UB, Ref is left dangling after the r-value expression is resolved. 

Why should we refrain from returning non-const references to private members? ;; Because you can directly change the value of the returned reference without having to deal with the access control system. 

True or false: Const member functions can’t return non-const references to data members ? ;; True, intuitively this makes sense because const member functions cannot change the state of the object so it would make sense that there is a mechanism which stops them from returning something which may alter the state of the object. 

Which access layer composes a classes interface , public or private ? ;; Public. A classes "interface" is usually called it's public interface. 

Why shouldn't we utilize the private keyword with respect to structs ? ;; Structs do not and should not be utilized for implementing data hiding as that would defeat the purpose of their use as aggregates ( You usually want to use all the data you defined ). 

What are some benefits of data hiding ? ;; Helps us manage invariants better, also we can remove the concern of having to understand the implementation. We simply concern ourselves with manipulating the interface. It also becomes quite easy to change the implementation of some interface without having to change the interface. 

If we want good class design we should ? ;; Think about where the class invariants might occur and move all those places into private access layer. 


True or False : Constructors create objects ? ;; No, the compiler allocates the memory needed for the class, the constructor simply initializes the memory with some value . 

Does const effect an object in construction ? ;; No, If I have a const class I can still call its constructor to initialize its values. 

Can the constructor ever be marked as being const ? ;; No, This is because the constructor should be able to initialize portions of the class itself. 

In what order are the members of a class initialized ? ;; In the order they are defined. 


What is wrong with the following code snippet ![[Pasted image 20250523141521.png]]? ;; This results in UB, we try to initialize m_x with the value of m_y which isn't initialized until m_x is. It follows the way the it is defined. 

When a member initializer list has finished executing, the object is considered what ? Initialized.

When the function body of the constructor has been executed, the object is considered what ? Constructed. Constness ensues after this. 


True or false: Suppose `foo` takes in class `Foo` as a parameter. Based off this call expression, the argument passed into `Foo` is an l-value: `foo( { 1 , 2 } )` ( Assume `Foos` constructor takes two integers ). ;; False, the argument passed to `foo` is an anonymous object and is an r-value whose lifetime is equivalent to the call site of foo. 


What is a narrowing conversion ? ;; A conversion wherein the type of target ( return value ) is less than the type of the object we are casting from. 

Give an example of a narrowing conversion ;; double to int ( 8 bytes to 4 ). Depends on implementation of course. 

When should we prefer `static_cast` ? ;; When we want to create a temporary object and need to perform a narrowing conversion. We want to make it really obvious that we're converting to a type that will result in some different behavior ( e.g a `char` to an `int` ). We want to use direct-initialization for some reason (e.g. to avoid list constructors taking precedence).

What is the copy constructor ? ;; A **copy constructor** is a constructor that is used to initialize an object with an existing object of the same type. After the copy constructor executes, the newly created object should be a copy of the object passed in as the initializer.

True or false: Similar to a default constructor, the compiler generates a default copy constructor for every class object we declare. ;; True. 


What mechanism does copy construction utilize to initialize member variables ? ;; It utilizes memberwise initialization. 

How can we define our own copy constructor? ;; `<Classname>( const <Classname>& x)`


What Constructor is called when an object is passed in by value ? ;; The copy constructor. 

What constructor is used to create temporary objects ? ;; The copy constructor. 

True or False: we can explicitly request the compiler to generate a copy constructor ourselves ( if so how ) ? ;; True , we can utilize the ` = default` keyword to do this.


How can we make our objects Non-copy constructible ? ;; Through deleting the copy constructor. 

What is the rule of three ? ;;  If a user defined object needs a user defined default constructor, a copy constructor, or copy assignment operator, then it requires all three.

The parameter for a copy constructor must be a (const) reference. Why aren’t we allowed to use pass by value? ;; If the copy constructor used pass by value, the copy constructor would need to call itself to copy the initializer argument into the copy constructor parameter. But that call to the copy constructor would also be pass by value, so the copy constructor would be invoked again to copy the argument into the function parameter. This would lead to an infinite chain of calls to the copy constructor.

True or False: Any call to a function passing an object by value calls the copy constructor ? ;; True. 