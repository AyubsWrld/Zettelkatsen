#### Data structure Definition questions
1. What best defines an array?
	1. A collection of like items stored contiguously within memory .  When we say that they are like items , this implies that they are the same datatype . Fundamentally what differentiates [[Datatypes]] are their size . 
2. Which of the following is not a property of arrays?
>	a. Its elements have the same type 
	===b. Its elements occupy different number of bytes==
	c. Its elements are stored in contiguous memory locations 
	d. Elements can be accessed in the same amount of time regardless of their position in the array

 3. For which of the following sequences would an array representation be most inefficient?
	a. strings - By definition is an array so no 
	b. stacks - Only specifies how 
	c. queues
	d. linked lists - Probably the most inefficient 

#### Euclidean Algorithm Pattern
**$a = bq + r$**

**Recursive Form** : 

```c
int euclid(int b , int r){
	if(0 == r){
		return b 
	}
	return euclid(r  , b % r)
}
```
 
 
#### Writing out algorithms . 
1. **Signature** : *Algorithm algorithmExample(arguments)*
2. **Purpose** : *This algorithm performs this purpose*
3. **Input** : *An explanation of the arguments taken by the algorithm*
4. **Output** : *An explanation of the outputs the algorithm produce* 
**Example (1)** , writing a matrix algorithm . 
___
**Algorithm**: $X(A[0...n] , n)$
**Purpose**: Returns the sum of of a matrix's contents skipping every n-1 value 
**Input**: An array , A  , and its length , n 
**Output**:  and integer whose sum is the matrixes contents skip counted by n-1 
$m \leftarrow l$
$i \leftarrow n$

$while \ i \geq 1 \ do$
	$m \leftarrow m\cdot A[i]$
	$i \leftarrow  i - \ 2$
$return \ m$
#### Analyzing an algorithm based on its implementation 
Given this algorithm , give it an efficiency class . 
$m \leftarrow l$
$i \leftarrow n$

$while \ i \geq 1 \ do$
	$m \leftarrow m\cdot A[i]$
	$i \leftarrow  i - \ 2$
$return \ m$


___ 
 Tags : #programming #algorithms 
 