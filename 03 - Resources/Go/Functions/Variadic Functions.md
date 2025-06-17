Functions which take a varying number of arguments of a singular type ( although type can vary as well through using generics ). 


```go
func sum(vals ...int) int {
	/* Do some work */
}
```

Variadic functions are made possible through the use of slices. Anytime a variadic function is called, an array is implicitly created, its arguments are then passed into the array, and then a slice is created using the values of the array and that is passed into the function. 


```go
func sum(vals ...int) int {
	/* Do some work */
}

x := []int{ 1 , 2 , 3 } 

sum( 1, 2, 3 ) 

sum( x... )  // Unpacking the slice, same as the first call.

```

Although they behave the same, the type of a function which takes a slice and a function which takes a varying amount of arguments are different 



#### Questions you should be able to answer.
___
Difference between type of variadic function and slice function. 
____
Tags: #programming #golang #language #go-http