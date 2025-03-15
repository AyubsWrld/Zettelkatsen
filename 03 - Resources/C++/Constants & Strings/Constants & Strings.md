- **Constants** are variable whos values don't change

- **Two types of constants** :
	- **Named constants**
	- **Literal constants** 

- **Constants should be used when you know a value of a variable isn't going to change** 

- **Use prefix 'k' to specify constants**  : `kGravityForce` , 'kPi' 

- **cv-qualifiers** delineate whether a variable is subject to change ( `volatile`) or not ( `const` )

- **Volatile** keyword instructs the compiler to refrain from attempting to optimize anything . 

- **Refrain from using non-descriptive numbers** ( *Magic numbers* )

- **Binary Literals** :  `0b` prefix ( 0b0001'0001 ->  0001 0001 ) 

- **Hexadecimal Literals** : ` 0x` prefix ( 0xFFFF -> 1111 1111 1111 1111 ) 

- **Can use std::bitset<8> to set binaries .**

- **Optimization is the process of modifying software to make it work more efficiently** 

- A **Profiler** is a program which keeps track of how long each part of the program takes to run .

- the **as-if rule** states that the compiler can optimize the code so long as it does not effect the programs observable behavior . 

___
Tags : #programming #cpp 