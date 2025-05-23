
___
Tags: #cpp #programming
___


What is RTTI ? ;; Run-time Type Information. 

How is RTTI Implemented ? ;; Using Virtual Tables. 

How are Virtual Tables created? ;; When a function is marked Virtual any child which inherits from said class has a virtual table which stores an array of pointers in memory pointing to different structures of data regarding the class. 

what does .quad do in the context of virtual tables ? ;; Compiler directive typically used to work with 64bit wide locations in memory. With respect to virtual tables it is usually used to store pointers to functions or other arrays which store type information about the owner of the virtual table. 


What is `rsp` ? ;; Stack pointer, points to the top of the current stack of the processes memory. 

What is function inlining ? ;; Optimization technique used by the compiler to expand a functions contents at the call site as opposed to branching. 


When can't function inlining occur ? ;; When the compiler does not have complete context of the function. 

What does the `call` command do ? ;; Saves procedure linking information on the stack and branches to the called procedure specified by the target operand. 

