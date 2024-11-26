#### Alternating Glasses
___
 There are 2n glasses standing next to each other in a row, the first n of them filled with a soda drink while the remaining n glasses are empty. Make the glasses alternate in a empty filled empty  pattern in the minimum number of glass moves. Show a decrease by constant and conquer algorithm.

Suppose $n=4$ , Endpoints are always in the correct order .

$M(n) = M(n-2)+1$ 
$M(n) = M(n-4)+1$ 
$M(n) = M(n-2i)+1$ 
$M(n) = M(n-1)/2$ 
$M(n) = \lfloor{n/2}$ 
 ___
 Tags : #programming #algorithms 