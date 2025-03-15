```javascript
function errorCallback(){
  console.log("Value failed");
  return false
}
function first() {
  return new Promise( (resolve) => {
    setTimeout(() => {
      console.log("first done");
      resolve("Yes") ;
    }, 100 );
  })
}

function second( value ) {
  console.log(value);
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