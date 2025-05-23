```cpp

void doSomething(){

}

int main(){
	volatile int n = 1 ; 
	volatile int y = 3 ; 

	n = y ;  // Has to be done here, compiler can't reorder the call ? 
	doSomething();  // Sequence point ? 
	
}
```
___
Tags : #programming #cpp #cpp17