A **function** that **remembers** the variables from the **lexical scope** in which it was **defined**, even after that scope has exited.

```javascript
function outer() {
  let x = 10;
  return function inner() {
    console.log(x); // inner "remembers" x
  }
}

let closure = outer();
closure(); // prints 10
```
____
Tags: #programming #golang #language #go-http