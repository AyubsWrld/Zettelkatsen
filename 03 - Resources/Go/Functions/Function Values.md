Functions are [[First-class Values]] in Go, they can be passed, assigned and returned like any other value in Go. The zero value of a function is nil and calling a nil function value causes a panic. 

```go
var f func(int) int ;
f(3) ; // Casues a panic. 

if f != nil {
	f(3) ; // Good.
}
```

#### Exercises
___
Write a function expand(s string, f func(string) string) string that replaces each substring ‘‘$foo’’ within s by the text returned by f("foo").
____
Tags: #programming #golang #language #go-http