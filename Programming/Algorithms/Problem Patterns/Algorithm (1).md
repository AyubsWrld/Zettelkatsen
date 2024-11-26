
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

###### b. Check if d is divisible by 16^i, where i is an integer, 0<= i <=n-1.
 
```c
Algorithm: IsDivisibleByPowerOf16
Input: A - array of hexadecimal digits
       n - size of the array A
       i - power of 16 to check divisibility by (0 <= i <= n-1)
Output: Boolean - true if the number is divisible by 16^i, false otherwise

// Check if i is within the valid range
if i < 0 or i >= n then
    return false  // Invalid input

// Check if the last i digits are all zeros
for j = n - 1 downto n - i do
    if A[j] != 0 then
        return false

return true
``` 

c.
```c
Algorithm: DivideBy256
Input: A - array of hexadecimal digits
       n - size of the array A
Output: B - new array storing d/256
        m - size of the new array B

// Initialize variables
m = max(1, n - 2)  // New size will be at least 1, or 2 less than original
B = new array of size m

// If the number is less than 256, the result is 0
if n <= 2 then
    B[0] = 0
    return B, 1

// Process the division from left to right
for i = 0 to n - 3 do
    B[i] = A[i]

// Remove leading zeros
while m > 1 and B[0] = 0 do
    Shift B left by 1 position
    m = m - 1

return B, m
```
 ___ 
 Tags : #programming #algorithms 