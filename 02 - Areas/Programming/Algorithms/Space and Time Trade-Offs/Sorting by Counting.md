As a first example of applying the input-enhancement technique. One rather obvious idea is to count, for each element of a list to be sorted, the total number of elements smaller than this and record the result within a table . 


Here we have our values within a table . 
```javascript
let values = [62, 31, 84, 96, 19, 47];
```


We instantiate an empty array with 0's of length equivalent to our other array 
```javascript
let count = new Array(values.length).fill(0); 
```

For every item in the outer loop we compare the items to the left of it . The one with the greater value has their count incremented within the list . 
```javascript
for (let i = 0; i < values.length - 1; i++) {
  for (let j = i + 1; j < values.length; j++) {
    if (values[i] < values[j]) {
      count[i] += 1; 
    } else {
      count[j] += 1;
    }
  }
}
```

lastly assign the values into a new array with the sizing equivalent 

```javascript
let s = new Array(values.length);
for (let i = 0; i < values.length; i++) {
  s[count[i]] = values[i];
}

console.log(s);

```


___

Tags : #programming #algorithms 