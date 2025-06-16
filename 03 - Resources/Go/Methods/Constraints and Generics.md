## 🔹 Why Use Generics?

Before generics, you'd either:

- Use `interface{}` (lose type safety)
    
- Duplicate code for different types
    

With generics, you can **abstract over types** without sacrificing safety or performance.

---

## 🔹 Basic Syntax

### ✅ Generic Function

```go
func PrintSlice[T any](s []T) {
    for _, v := range s {
        fmt.Println(v)
    }
}
```

- `T` is a **type parameter**.
    
- `any` is a type constraint (alias for `interface{}`).
    
- You call it like:
    
    ```go
    PrintSlice([]int{1, 2, 3})
    PrintSlice([]string{"a", "b"})
    ```
    

---

## 🔹 Generic Types

```go
type Stack[T any] struct {
    items []T
}

func (s *Stack[T]) Push(v T) {
    s.items = append(s.items, v)
}

func (s *Stack[T]) Pop() T {
    l := len(s.items)
    val := s.items[l-1]
    s.items = s.items[:l-1]
    return val
}
```

You can create different stacks:

```go
s1 := Stack[int]{}
s2 := Stack[string]{}
```

---

## 🔹 Type Constraints

You can **restrict the types** that can be passed in using **interfaces**.

### Example: Comparable types only

```go
type Comparable interface {
    ~int | ~float64 | ~string  // allow underlying types
}

func Max[T Comparable](a, b T) T {
    if a > b {
        return a
    }
    return b
}
```

- `~int` means: any type whose underlying type is `int`.
    
- This is part of the **type set** concept.
    

---

## 🔹 Interface Constraints vs. Type Sets

- `interface{}` (aka `any`) = accepts all types
    
- Custom constraints (with `|` or methods) limit acceptable types
    

```go
type Adder interface {
    Add(T) T
}

func Sum[T Adder](a, b T) T {
    return a.Add(b)
}
```

---

## 🔹 Instantiating Generic Code

The Go compiler **generates specialized versions** of generic code for each used type. It's **monomorphized**, not boxed or reflection-based (like in Java or older Go interface tricks). This keeps performance tight.

---

## 🔹 Gotchas & Tips

- Generics can’t replace all interface use cases (e.g., dynamic dispatch).
    
- You can't use operators like `+`, `==` unless the constraint guarantees they’re valid.
    
- Type inference is powerful; often you don’t need to specify `[T]`.
    

---

## 🔸 Summary

|Concept|Example|
|---|---|
|Generic function|`func Identity[T any](v T) T { return v }`|
|Generic struct|`type Box[T any] struct { value T }`|
|Type constraint|`type Number interface { ~int|
|Inference|`Identity(42)` — Go figures out `T`|

---

Would you like to see how generics compare with interfaces in real-world design (like with repositories, middleware, etc.)?
____
Tags: #programming #golang #language 