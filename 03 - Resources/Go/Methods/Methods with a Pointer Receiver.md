Used in the case when we need to alter the state of the receiver. In the normal case the receiver is passed by value and a copy is made for the lifetime of the function. By passing by value we can side step this copying and use the receiver itself. 

```go

type Point stuct { X float32 ; }

func ( p *Point ) doSomething( x int ){
	p.X = x ;  // Alters x itself. 
}

// (*Point).doSomething can be called by providing a *Point Receiver. 

r := &Point{1, 2} ; 
r.doSomething(3) ; 

// or this 

p := Point{1, 2}
pptr := &p ; 
pptr.doSomething(3) ; 

//or this 

p := Point{1, 2}
(&p).doSomething(3)

// Shorthand ( Preferred ) 

p.doSomething(3) // Implicitly pass by reference to doSomething. 
```

Named types and pointers to them are the only types that may appear in a receiver declaration. Also to avoid ambiguities, method declarations are not permitted on named types that are themselves pointers. 
____
Tags: #programming #golang #language 