Array whose size is fixed at compile time . The memory for the array is allocated at a specific location in memory ( Usually the program's data segment ) , it remains allocated throughout the entire run-time of the application . 

#### Example 
___

```c
struct IntValue {
	int value ; 
};



static struct IntValue Number[3] = {
	{10} , 
	{10} , 
	{10} , 
}

for(int idx = 0 ; idx < 3 ; idx++){
	printf("Number[%d] : %d" , i , Number[i].value) ;
}
```
___
Tags : #programming #c #language 