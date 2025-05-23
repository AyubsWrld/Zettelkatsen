##### Member functions returning references to data members.
- Prefer const l-value references to data objects which are private members. 
- A member function returning a reference should return a reference of the same type as the data member being returned, to avoid unnecessary conversions.
- An rvalue object is destroyed at the end of the full expression in which it is created. Any references to members of the rvalue object are left dangling at that point.
```cpp

class Person
{
	std::string m_name ; 

	Person( std::string name ) : m_name( name ) {} 
public:
	const std::string& getName() const
	{
		return m_name ;  // Returns const lvalue reference to m_name
	}
}

Person createPerson()
{
	return Person( "Ayub" ) ; 
}

int main()
{
	const std::string& name = createPerson().getName() ;  // Expression 
	std::cout << name << std::endl ; // Dangling, Person doesn't exist
}
```

- Avoid returning non-const references to private members, otherwise this will cause us to subvert the access control system. 
---
##### Separation of Concerns: Implementation vs. Interface
- Classes offer a really easy way to separate public interfaces from implementation. Whatever is in the public access layer makes up our interface whereas everything in private access layer makes up our implementation. 
- **Data Hiding** is the process of separating interface from implementation through making parts of an object inaccessible to the user. 
- Structs do not and should not be utilized for implementing data hiding as that would defeat the purpose of their use as aggregates ( You usually want to use all the data you defined ). 
- Prefer implementing functions as non-members when possible (especially functions that contain application specific data or logic).

##### Constructors
- Constructors do not create the object, the compiler is in charge of allocating the memory needed to hold the class object. The constructor is then called to initialize the allocated memory. 
- Objects under construction are not effected by const qualification. 
- Constructors cannot be const. 
- Constructors must have the same name as the class being constructed. 
- We assign member variables utilizing list initialization. 
- Members in a member initializer are always initialized in the order in which they are defined inside the class. 
- Member variables in a member initializer list should be listed in order that they are defined in the class.
- It’s also a good idea to avoid initializing members using the value of other members (if possible). That way, even if you do make a mistake in the initialization order, it shouldn’t matter because there are no dependencies between initialization values.
- Once the member initializer list has finished executing, the object is considered initialized. Once the function body has finished executing, the object is considered constructed.
- We can use the inside of a constructor body to handle class invariants. 
___
Tags: #cpp #programming