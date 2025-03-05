
**1. What are Closures?**
   - Closures are self-contained blocks of functionality that can be passed around and used in your code.
   - They can capture and store references to variables and constants from the surrounding context in which they are defined.
   - Closures in Swift are similar to lambdas or anonymous functions in other programming languages.

**2. Types of Closures:**
   - **Global Functions:** These are closures that have a name and do not capture any values.
   - **Nested Functions:** These are closures that have a name and can capture values from their enclosing function.
   - **Closure Expressions:** These are unnamed closures written in a lightweight syntax, often used inline.

**3. Basic Syntax:**
   ```swift
   { (parameters) -> returnType in
       // code
   }
   ```
   - Parameters are defined in parentheses.
   - The return type is specified after the `->` arrow.
   - The `in` keyword separates the parameters and return type from the closure body.

**4. Inferring Types:**
   - Swift can infer the types of parameters and return values, allowing you to omit them.
   - Example:
     ```swift
     let add = { (a: Int, b: Int) -> Int in
         return a + b
     }
     ```

**5. Shorthand Argument Names:**
   - Swift automatically provides shorthand argument names, like `$0`, `$1`, etc., for closures that omit parameter names.
   - Example:
     ```swift
     let multiply = { $0 * $1 }
     ```

**6. Trailing Closure Syntax:**
   - When a closure is the last argument to a function, it can be written outside the function's parentheses.
   - Example:
     ```swift
     func performOperation(operation: () -> Void) {
         operation()
     }

     performOperation {
         print("This is a trailing closure")
     }
     ```

**7. Capturing Values:**
   - Closures can capture and store references to variables and constants from the surrounding context.
   - If a closure captures a reference to an object, it can lead to a strong reference cycle if not managed properly.

**8. Escaping Closures:**
   - Closures are non-escaping by default, meaning they cannot be stored outside of the function they're passed to.
   - An escaping closure is one that can be stored and executed later, requiring the `@escaping` keyword.
   - Example:
     ```swift
     func executeLater(completion: @escaping () -> Void) {
         DispatchQueue.main.async {
             completion()
         }
     }
     ```

**9. Autoclosures:**
   - An `@autoclosure` automatically creates a closure from an expression that is passed as an argument.
   - Often used to defer expensive computations until they are actually needed.

**10. Common Use Cases:**
   - **Callbacks**: Passing completion handlers in asynchronous operations.
   - **Higher-Order Functions**: Functions like `map`, `filter`, and `reduce` that take closures as arguments.
   - **Event Handling**: Handling user interactions or system events with closures.

### Key Points:
- Closures are powerful, flexible tools for functional programming in Swift.
- They can capture and manipulate the state from their enclosing context.
- Swift’s syntax allows closures to be concise, making them ideal for passing small functions around in your code.
___

Tags : #swift #language 