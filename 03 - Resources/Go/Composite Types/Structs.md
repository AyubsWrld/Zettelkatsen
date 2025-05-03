_____
##### Introduction:

Similar to how structs are within other languages. Simple aggregate data types. 

```go
type Employee struct {
	Name string ; // Referencable outside of package.
	id   int    ; // Only occurs within package itself.
}
```

Structs are [[ Comparable ]] $iff$ all of their members are comparable. 

_____
##### Struct Literals:

Struct literals in Go can be defined using two forms: one requires specifying all field values in the correct order, making the code fragile to changes, while the other allows named fields to be assigned in any order, making it more flexible and readable. Structs can be passed as function arguments, returned from functions, and often handled via pointers for efficiency and modification, using shorthand notation for initialization.

```go
type Point struct{ X, Y int} // Referencable outside of struct.
```

_____
###### Struct Embedding and Anonymous Fields: 

In Go, struct embedding allows you to include one named struct type as an **anonymous field** within another struct, enabling a kind of lightweight inheritance and **syntactic shorthand**. When you embed a struct (e.g., `type Circle struct { Point; Radius int }`), its fields are promoted to the outer struct (`Circle.X`, `Circle.Y` instead of `Circle.Point.X`, `Circle.Point.Y`). You can then embed `Circle` again in another struct like `Wheel`, allowing access to deeply nested fields with simple dot notation (`w.X` instead of `w.Circle.Point.X`). For example, with `type Wheel struct { Circle; Spokes int }`, you can write `w.Radius = 5` and `w.X = 8`, which is equivalent to `w.Circle.Point.X = 8`. However, this shorthand does **not** apply to struct literals — you must fully specify the embedded structure when initializing (`Wheel{Circle{Point{8, 8}, 5}, 20}`). While fields from embedded types are accessible as if they were part of the outer struct, if multiple embedded structs have the same field name, Go will report a conflict and require disambiguation (e.g., `w.Circle.Radius` vs `w.AnotherCircle.Radius`). Importantly, embedding also **promotes methods**, allowing the outer struct to inherit the behavior of the embedded type — a core idiom in Go for code reuse and composition.

____
Tags : #programming #golang #language #go