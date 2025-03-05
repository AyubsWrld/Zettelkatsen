Iterating across objects to retrieve `key` : `value` pairs works as follows 
```javascript
const adjacencyList = {
	'A' : 1 , 
	'B' : 2 , 
	'C' : 3 , 
}

for( const [ key , value ] of Object.entries(adjacencyList)){
	console.log(`${key} : ${value}`) ; 
}
```

This directly references the Object class' entries method 

___
Tags : #programming #javascript #language 