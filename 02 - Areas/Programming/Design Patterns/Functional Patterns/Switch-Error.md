> [!error] 
>  
This pattern uses a `switch` statement to handle different error codes in an `async` function's `catch` block, assigning user-friendly messages based on the error type for clearer feedback. It's concise, easy to read, and maintainable.

```js
let message = 'Failed to get authorization';
switch (error.code) {
  case 'AUTH_DENIED':
    message = 'Authorization was denied. Please enable Screen Time in Settings.';
    break;
  case 'AUTH_CANCELED':
    message = 'Authorization was canceled. Please try again.';
    break;
  // Additional cases...
  default:
    message = 'An unknown error occurred.';
}
```


___

Tags : #design-patterns #functional-pattern #programming #error-handling