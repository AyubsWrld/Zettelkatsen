[[Collection Type]] which encapsulates its members within `square brackets ( [ ] )` . 

#####  Implementation 
___
```swift
var someInts : [Int] = [ 1 , 2 , 3] ; 

```

##### Indexing 
___
`Indexing` is done utilizing the `[]` operator . Returns `n-th` variable within the brackets . 

```swift
var someInts : [Int] = [ 1 , 2 , 3] ; 
print(someInts[1])  ; // prints 2  

```
##### Array Concatenation 
____
```swift
var someInts : [Int] = [ 1 , 2 , 3 , 4 ] ; 
var someIntsTwo : [Int] = [ 1 , 2 , 3 , 4 ] ; 
var concat : [Int] = someInts + someIntsTwo ; 
print(concat) ; 
```
##### Retrieving the number of members within Array 
___
Utilize the `.count` method to retrieve the number of members within the array . 
```swift
var someInts : [Int] = [ 1 , 2 , 3 , 4 ] ; 
print(someInts.count); // reutrn 4 
```

##### `nil` check 
___
Utilize the `.count` method to retrieve the number of members within the array . 
```swift
var someInts : [Int] = [ 1 , 2 , 3 , 4 ] ; 
if(someInts.isEmpty){
	print("Array is empty") ; 	
}
else{
	print("Array has length \(someInts.count)") ; 
};
// prints Array has length 4
```

##### Walking an Array 
___
We can utilize the range method to iterate over the array 
```swift 
var someInts : [Int] = [ 1 , 2 , 3 , 4 ] ; 
for number in someInts { 
	print(number);  
}
```

##### appending from arrays
___
Utilize the `.count` method to retrieve the number of members within the array . 
```swift
var someInts : [Int] = [ 1 , 2 , 3 , 4 ] ; 
someInts.append(5) ; 
print(someInts[4]) ; 

// Prints 5 .
```
____


Tags : #language #swift #programming