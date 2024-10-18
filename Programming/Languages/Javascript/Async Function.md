### JavaScript Statements & Declarations Overview

#### 1. **Async Function**
- **Definition**: The `async function` declaration creates an asynchronous function, which returns a promise.
- **Key Points**:
  - The `await` keyword can be used inside async functions to pause execution until the awaited promise resolves.
  - The function always returns a promise, which can resolve to the returned value.
  - Syntax:
    ```js
    async function functionName(param1, param2) {
      // code
    }
    ```

#### 2. **Block Statement**
- **Definition**: A group of zero or more statements enclosed in curly braces `{}`.
- **Usage**: Commonly used with control flow statements like `if`, `for`, `while`.
  
#### 3. **Break**
- **Definition**: Exits a loop or switch statement early.
  
#### 4. **Class**
- **Definition**: A blueprint for creating objects with predefined methods and properties.
- **Syntax**:
  ```js
  class ClassName {
    constructor() { ... }
    methodName() { ... }
  }
  ```
  
#### 5. **Const**
- **Definition**: Declares a block-scoped, read-only constant.
  
#### 6. **Continue**
- **Definition**: Skips the current iteration of a loop and continues with the next iteration.
  
#### 7. **Debugger**
- **Definition**: Pauses the execution of JavaScript and invokes any debugging functionality available.
  
#### 8. **Do...While**
- **Definition**: Executes a block of code once and then repeats execution as long as a specified condition is true.
  
#### 9. **Empty Statement**
- **Definition**: A semicolon (`;`) without any accompanying code. Does nothing.

#### 10. **Export**
- **Definition**: Allows a module to export its functions, objects, or values to be used in other files.
  
#### 11. **Expression Statement**
- **Definition**: Any valid JavaScript expression followed by a semicolon. Often used to execute expressions like function calls.

#### 12. **For**
- **Definition**: Creates a loop with three optional expressions:
  - Initialization
  - Condition
  - Increment/Decrement
  
#### 13. **For Await...Of**
- **Definition**: Works like a `for...of` loop, but handles asynchronous iteration of promises.
  
#### 14. **For...In**
- **Definition**: Iterates over all enumerable property names of an object.
  
#### 15. **For...Of**
- **Definition**: Iterates over values of iterable objects (like arrays, strings).

#### 16. **Function Declaration**
- **Definition**: Defines a named function that can be called by its name.
  
#### 17. **Function*** 
- **Definition**: Declares a generator function, which can return multiple values over time.

#### 18. **If...Else**
- **Definition**: Executes a block of code if a specified condition is true; otherwise, an alternative block is executed.
  
#### 19. **Import**
- **Definition**: Used to import functions, objects, or values from another module or file.
  
#### 20. **Labeled Statement**
- **Definition**: Provides an identifier to a statement, allowing the program to break or continue that label specifically.

#### 21. **Let**
- **Definition**: Declares a block-scoped variable that can be reassigned.
  
#### 22. **Return**
- **Definition**: Ends function execution and optionally specifies a value to return to the function caller.
  
#### 23. **Switch**
- **Definition**: Evaluates an expression and executes the corresponding case block depending on its value.
  
#### 24. **Throw**
- **Definition**: Throws a custom error that can be caught by `try...catch`.

#### 25. **Try...Catch**
- **Definition**: Handles exceptions that may occur during the execution of a block of code.
  
#### 26. **Var**
- **Definition**: Declares a function-scoped or globally-scoped variable. Not recommended due to scoping issues.
  
#### 27. **While**
- **Definition**: Loops as long as the specified condition is true.
  
#### 28. **With** (Deprecated)
- **Definition**: Extends the scope chain for a statement. Not recommended due to potential ambiguity and performance issues.

---

### Additional JavaScript Concepts

#### Functions
- Functions encapsulate code that can be invoked.
- Can be declared using function declarations or expressions.

#### Classes
- Classes define objects with properties and methods.
  
#### Regular Expressions
- Patterns used to match character combinations in strings.

#### Errors
- JavaScript supports various types of errors like `SyntaxError`, `TypeError`, and custom errors thrown with `throw`.



____

Tags : #javascript