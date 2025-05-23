Refers to whether our class object ( Union , Struct , Class ) are in an semantically invalid state. This leads to undefined behavior. For example.

```cpp
struct Fraction
{
	int numerator { 0 }; 
	int denominator { 1 };  // Default values. 
}

int main( int argc , char* argv[]){
	Fraction f{ 5 , 0 } // Divide by zero undefined. 
	return 0;
}
```

___
Tags: #cpp #programming