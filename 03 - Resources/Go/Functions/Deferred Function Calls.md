Defers a function call to the end of the enclosing [[Lexical Scope]]. The function and argument expressions **are evaluated when the statement is executed**, but the actual call is deferred until the function that contains the defer statement has finished, whether normally, by executing a return statement or falling off the end, or abnormally, by panicking. 


It is commonly used to :
- **Unlock a mutex**.
- **Close a file**.
- **Close a network connection**.
- Or really any Clean up. 

#### Altering Returned Values
___
It is also worth noting that functions marked as `defer` have the ability to access values being returned by the enclosing function. For example: 

```go
//Returns square + 1. 
func doWork(x int) (result int){
	defer func() { result += 1 ; }
	return x * x ; 
}
```
____
Tags: #programming #golang #language #go-http