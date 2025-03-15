Used to stop [[Overload Resolution]] when unwanted.  

```cpp 
void printInt( int x ) 
{

}

void printInt(char)  = delete ; // Removes call 
void printInt(bool)  = delete ; // Removes call 


int main()
{
	printInt("w") ; // Numeric Promotion would occur here 
	printInt(false) ; // Numeric Promotion would occur here 
	printInt(5) ; // Only one we want 
}
```

This however is quite verbose. If we want to remove any calls to a function of different types than the one specified we can utilize [[Template Functions]] to achieve this. 
___
Tags :  #cppfunctions 
