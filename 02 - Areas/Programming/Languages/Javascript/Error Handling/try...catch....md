- **`try` block**: The code that might throw an error is wrapped inside the `try` block. The `try` block runs the code, and if it encounters an error (also known as an exception), it immediately stops execution and jumps to the `catch` block.
    
- **`catch` block**: If an error occurs in the `try` block, the `catch` block is executed. It allows you to handle the error gracefully (e.g., log the error, show an error message to the user, or perform some fallback behavior).
    
- **`finally` block** (optional): The `finally` block is always executed, whether an error occurs or not. It’s often used to clean up resources (like resetting a loading state, closing files or connections, etc.).

```javascript
try {
  // Code that might throw an error (like fetching from a database)
} catch (error) {
  // Handle the error
} finally {
  // Clean up or finalize operations (optional, but runs no matter what)
}
```

____

Tags : #javascript