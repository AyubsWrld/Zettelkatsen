##### Observe the following code snippet...

```c

void increment( int* x, int* y ){
	*x = 1 ;
	*y = 2 ;
}

int x ;

increment( &x, &x ); 

```

This is perfectly legal. The compiler is not allowed to reorder the writes because the result would be different. Because of this the compiler must assume that the a call to `increment()` the values might be the same so there cannot be any reordering done. So no additional optimizations. 

However if the two types have different types then the compiler can assume that they do not point to the same thing and in fact can do any optimizations. 

```cpp
void increment( int* x, float* y ){
	*x = 1 ;
	*y = 2 ;
}

int x ;

increment( &x, reinterpret_cast(float* ) &x ); 
```

This is undefined behavior however. 

___
Tags : #programming #cpp 