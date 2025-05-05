
**Promise** work similarly to how conditional statements in set theory work . 

$$\text{condition} \rightarrow \text{boolean}$$

```javascript
let p = new Promise((resolve , reject) =>{ // Arrow Function 
	let boughtCandy = true ;  // Some condition 
	if(boughtCandy){ // Case the condition resolved to true 
		resolve('Success') ;  // The promise is resolved ( The promise is kept )
	}else{ // case the condition is false 
		reject('Error') // The promise is rejected ( the promise is broken )
	}
})
```



```javascript
p.then((message) => {
	console.log('Promise was kept ' + message)
}).catch((message) => {
	console.log('Promise was not kept ' + message)
})
```
____

Tags : #javascript