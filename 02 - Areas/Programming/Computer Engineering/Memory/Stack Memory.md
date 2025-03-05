Location of memory used to store Local Variables declared inside of functions as well as function call information . 
#### Characteristics 
___
- Stack memory is automatically managed . That is everything is allocated and deallocated automatically when a function is called or returns . 
- The size of the stack is limited and is smaller in comparison to the size of the heap . 
- The stack memory is faster to allocate and access because it follows a [[Stack]] Data structure .
- Stack memory is short lived , and values allocated onto the stack have a life cycle of the scope of the function 

#### Example : 
```c
void myFunction() {
    int a = 10;  // 'a' is stored on the stack
}
```

`a` is stored onto the stack and is freed once `myFunction() exits` . 
____

Tags : #computer-architecture 