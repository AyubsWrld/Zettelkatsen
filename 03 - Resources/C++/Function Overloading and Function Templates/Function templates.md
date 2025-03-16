Used to combat the verbosity of having to define multiple different functions with similar purposes. 

<center> as opposed to</center>
```cpp 
int getMax( int x , int y )
{
	return x > y ? x : y ; 
}

double getMax( double x , double y )
{
	return x > y ? x : y ; 
}
```

<center>We do this instead</center>

```cpp
template <typename T> 
T getMax( T x , T y )
{
	return x > y ? x : y ; 
}
```


___
Tags :  #cppfunctions 