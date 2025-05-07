An instance of an interface implementation is actually a pointer to an array of pointers to methods - that is, a function table that refers to an implementation of all of the methods specified in the interface. Once a client has this pointer to the array of pointers to functions it can call any of the functions it desires. 

Its far more convenient to refer to this array of function pointers as the [[Interface Pointer]]. Because an interface is a type, the compiler, given the names of methods, can check the types of parameters and return values of each interface method call.

Each interface is an immutable contract of a functional group of methods. You reference an interface at runtime with a globally unique interface identifier ( IID ). This IID, allows a client to ask an object precisely whether it supports the semantics of the interface. 


____
Tags : #os #win32