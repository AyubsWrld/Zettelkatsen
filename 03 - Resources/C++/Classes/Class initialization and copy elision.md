There are three key differences between the initialization forms: 

- List initialization disallows narrowing conversions.
- Copy initialization only considers non-explicit constructors/conversion functions. We’ll cover this in lesson 
- List initialization prioritizes matching list constructors over other matching constructors. 


#### Copy elision 
___
Copy elision is a compiler optimization which removes unnecessary copies being made. When the compiler optimizes away a call to the copy constructor we ay that the constructor has been elided. 
___
Tags: #cpp #programming
