```go
typ := reflect.TypeOf(checking) 
iface := reflect.TypeFor[InterfaceToCheck]() satisfies := typ.AssignableTo(iface)
```

https://go.googlesource.com/proposal/+/master/design/generics-implementation-gcshape.md
____
Tags: #programming #golang #language 