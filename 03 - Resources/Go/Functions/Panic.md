Used to handle errors which occur at runtime. Normal execution stops, the stack is unwinded, and any and all functions marked as defer are executed in the reverse order they were defined in. For each goroutine, a stack trace showing the stack of function calls that were active at the time of panic is also printed. 

We can also cause a panic when some impossible case occurs within our code. 

```go
switch s := suit(DrawCard()); s {
case "Spades" :
case "Hearts" :
case "Clubs" :
case "Diamonds" :
default:
	panic(fmt.Sprintf("Invalid suit %q",s)) ; 
}
```

 Panics are usually reserved for unrecoverable errors. It is common practice to mark such functions which deal with Unrecoverable errors with the prefix `Must` ( ie `MustCompile` ). 


#### Illustration 
___

____
Tags: #programming #golang #language #go-http