If the built-in `recover` function is called within a deferred function and the function containing the defer statement is panicking, `recover` ends the current state of panic and returns the panic value. 

```go
func Parse() {
 defer func() {
	 if p := recover() ; p != nil {
		 err := fmt.Errorf("Internal error %v", p) ; 
	 }
 }
}
```

Error should be handled selectively in this manner if at all as recovering from a panic could leave resources in an undisclosed state. 

### Exercise 
___
1) Use `panic` and `recover` to write a function that contains no return statement yet returns a non-zero value.
____
Tags: #programming #golang #language #go-http