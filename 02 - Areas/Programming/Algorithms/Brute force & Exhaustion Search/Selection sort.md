Scan the array to find its smallest element and swap it with the first element 

#### Pseudo Code
___

**Algorithm** : *Selection Sort[0...n-1]* 
// Sorts given array by selection sort 
// Input : An Array of [0..n-1] of orderable elements
// Output: An Array of [0..n-1] sorted in nondecreasing order
```c
for i <- 0 to n - 2 do 
	min <- i // Set min to the current position 
	for j <- i + 1 to n - 1 do // Start with i + 1 for j check the next entry
		if A[j] < A[min] // if j is less than J then implement 
			min <- j 
	swap A[i] and A[min] 
```

- **Input Size:**  Length of the array 
- **Basic Operation**: Key Comparison 
___
Tags : #algorithms #math #programming 