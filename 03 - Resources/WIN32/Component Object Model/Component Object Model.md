**COM** stands for **Component Object Model**. It's a **Microsoft-developed binary-interface standard** for enabling **inter-process communication (IPC)** and **dynamic object creation** in a language-agnostic way on Windows.

**COM** specifies an object model and programming requirements that enable [[COM Objects]] to interact with other objects. 

COM is referred to as a _binary standard_; a standard that applies after a program has been translated to binary machine code.

The only requirement to create COM objects is that the language supports the creation of structure of points and either explicitly or implicitly, call functions through pointers.

Unlike a normal software object which is made up of a set of data and functions which manipulate the data, a COM object is one in which access to an objects data is achieved exclusively through one or more sets of related data. These functions are called interfaces, and the functions of an interface are called methods. COM requires that the only way to gain access to the methods of an interface is through a pointer to the interface.

Besides specifying the basic binary object standard, COM defines certain basic interfaces that provide functions common to all COM-based technologies, and it provides a small number of functions that all components require. COM also defines how objects work together over a distributed environment and has added security features to help provide system and component integrity.



____
Tags : #os #win32