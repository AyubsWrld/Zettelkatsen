Variables are declared using the `set` keyword. The first variable passed in is the name of the variable you wish to initialize and the variables following it are the values assigned to the variable. Values are stored in a string. 

```cmake 
set(Test "TESTVALUE") # Test has TESTVALUE within it 
set(Test 1)           # Test is assigned "1"
set(Test 1 2 3)           # Test is assigned "1;2;3" 
```
___
Tags : #programming #cmake