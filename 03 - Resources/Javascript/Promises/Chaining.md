>[!tldr]
>Used to handle asynchronous functions in a sequential manner- where each subsequent operation starts only when the previous one is successfully completed. 

> [!error]
> The problem we are addressing is [[Callback Hell]] 
> ```javascript
> doSomething(function (result) {
> doSomethingElse(result, function (newResult) {
doThirdThing(newResult, function (finalResult) {
  console.log(`Got the final result: ${finalResult}`);
}, failureCallback);
}, failureCallback);
}, failureCallback);
> ```

The solution to this is to utilize the `then()` function which returns a new promise, different from the original.

```javascript
const promise = doSomething() ; 
const promise2 = promise.then( successCallback , failureCallback) 
```

`promise2` not only represents the successful completion of `promise` of `successCallback` & `failureCallback` , but also `doSomething`. 

With promise chaining we can create a long chain of asynchronous operations in which each operation executes ( or does not execute ) after the previous one exits. 

>[!example]

```javascript

function errorCallback(){
  console.log("Value failed");
  return false
}
function first() {
  return new Promise( (resolve) => {
    setTimeout(() => {
      console.log("first done");
      resolve(true) ;
    }, 100 );
  })
}

function second() {
  return new Promise( (resolve) => {
    setTimeout(() => {
      console.log("second done");
      resolve(true) ;
    }, 100 );
  })
}
function third() {
  return new Promise( (resolve) => {
    setTimeout(() => {
      console.log("third done");
      resolve(true) ;
    }, 100 );
  })
}
function fourth() {
  return new Promise( (resolve) => {
    setTimeout(() => {
      console.log("fourth done");
      resolve(true) ;
    }, 100 );
  })
}


const value = await first()
  .then(second)
  .then(third)
  .then(fourth)
  .catch(errorCallback) ;

```

___
Tags : #programming #javascript 