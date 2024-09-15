
##### a. Check if d is divisible by 2. Solution must be in linear time 
```c
Algorithm: IsDivisibleByTwo
Input: A - array of hexadecimal digits
       n - size of the array A
Output: Boolean - true if the number is divisible by 2, false otherwise

// We only need to check the last digit to determine divisibility by 2
// Get the last digit (least significant digit)
lastDigit = A[n-1]

// Check if the last digit is even (0, 2, 4, 6, 8, A, C, or E)
if lastDigit is in {0, 2, 4, 6, 8, 'A', 'C', 'E'} then
    return true
else
    return false
```
 ___
 Tags : #programming #algorithms 