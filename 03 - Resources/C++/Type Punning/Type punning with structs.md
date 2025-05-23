Usually used when we want to copy structs of one type to another with varying paddings we must artificially add padding ourselves. 

```cpp


// 8 bytes bytes for alignment purposes + 2 bytes of padding. Single register 

struct A {
	char x ; 
	int  y ; 
} 

//  8 bytes for allignment purposes, 2 bytes of padding added. single register

struct B {
	int  y ; 
	char x ; 
}
```

However where the padding is 
___
Tags : #programming #cpp 