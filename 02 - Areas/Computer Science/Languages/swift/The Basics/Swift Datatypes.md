### Constants and Variables

- **Constants** and **variables** store values with names. 
  - Constants: Declared using `let`, their values cannot change once set.
  - Variables: Declared using `var`, their values can change.

### Declaration

- **Syntax**:
  - Constant: `let maximumNumberOfLoginAttempts = 10`
  - Variable: `var currentLoginAttempt = 0`
  
  Example:
  - `maximumNumberOfLoginAttempts` is constant (fixed at 10).
  - `currentLoginAttempt` is a variable (changes after each login attempt).

### Use Cases

- Use `let` for values that won’t change.
- Use `var` for values that can change.

### Initialization Later

- You can declare a constant or variable without an initial value, but it must be set before use.

```swift
var environment = "development"
let maximumNumberOfLoginAttempts: Int

if environment == "development" {
    maximumNumberOfLoginAttempts = 100
} else {
    maximumNumberOfLoginAttempts = 10
}
```

### Multiple Declarations

- Multiple variables or constants can be declared on one line:
  ```swift
  var x = 0.0, y = 0.0, z = 0.0
  ```


___

Tags : #swift #language 