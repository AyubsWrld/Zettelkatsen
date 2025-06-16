Methods are declared like normal functions except we have prefix the function name with the object the method belongs to. The parameter attaches the function to the type of that parameter.


```go
type Point struct {
	X float64 ; 
	Y float64 ; 
}

// (p Point) attaches the function Distance to to the point. 
func (p Point) DistanceTo( p* Point ) float32 {
	 /* Do some work */
	 return retval ; 	
}
```

The extra parameter `p` is called the method's receiver and it ties the method to the object. 

We can also define methods on type-aliased types themselves

```go
type Path []Point 

func (p Path) Walk() {
	/* Do some work */ 
}
```

This is similar to defining a method on a struct. 
____
Tags: #programming #golang #language 