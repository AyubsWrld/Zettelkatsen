- Instantiated using the built in `make` function 
- `p := make(map[Key-type]Value-type`.
- The zero value for a map is nil, that is, a reference to no hash table at all. 
 
```go
var ages map[string]int 
fmt.Println(ages == nil) // "true" 
fmt.Println(len(ages) == 0) // "true"
```
- Accessing a map element by subscripting always yields a value. If the key is present in the map, you get the corresponding value; if not,you get the zero value for the element type
____
Tags : #programming #golang #language #go