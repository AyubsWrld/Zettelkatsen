In Go, **enums** aren’t a built-in language feature like in some other languages (e.g., C++ or Java), but we can **simulate enums** using `const` blocks with a named type and the `iota` keyword.

---

### ✅ How Go "Enums" Work

#### 1. **Define a named type**

```go
type Mode int
```

This creates a new type named `Mode` based on `int`.

#### 2. **Use a `const` block with `iota`**

```go
const (
	Auto Mode = iota // 0
	Manual           // 1
	Off              // 2
)
```

- `iota` starts at 0 and increments automatically.
    
- Now you have named constants: `Auto`, `Manual`, and `Off` of type `Mode`.
    

---

### 📦 Why Use Enums in Go?

Enums:

- Make your code **more readable** and **type-safe**
    
- Help represent **a limited set of valid values**
    
- Can be used in **switch statements** and comparisons
    

---

### 🧠 Example Use

```go
type Mode int

const (
	Auto Mode = iota
	Manual
	Off
)

func describeMode(m Mode) {
	switch m {
	case Auto:
		fmt.Println("Automatic mode")
	case Manual:
		fmt.Println("Manual mode")
	case Off:
		fmt.Println("Turned off")
	default:
		fmt.Println("Unknown mode")
	}
}
```

---

### 💬 Optional: Add String Output

Go doesn’t give you string names automatically, but you can add this manually:

```go
func (m Mode) String() string {
	switch m {
	case Auto:
		return "Auto"
	case Manual:
		return "Manual"
	case Off:
		return "Off"
	default:
		return "Unknown"
	}
}
```

Then `fmt.Println(Auto)` would print `Auto` instead of `0`.

---

### 🔑 Summary

- Go doesn't have built-in enums, but you can **simulate them** with `const`, custom types, and `iota`.
    
- They're great for representing **sets of related options**.
    
- Add a `.String()` method for better printing/debugging.
    

Let me know if you want a generator like `stringer` to auto-generate the `String()` method!

____
Tags : #programming #golang #language #go