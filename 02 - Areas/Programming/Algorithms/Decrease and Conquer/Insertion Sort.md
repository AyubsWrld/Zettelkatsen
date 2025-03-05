```c
#include <stdio.h>

void insertionSort(int A[], int n) {
    int i, j, v;

    // Loop through each element in the array starting from the second one
    for (i = 1; i < n; i++) {
        v = A[i];  // Set the current value to be inserted
        j = i - 1; // Start comparing with the element just before

        // Shift elements of A[0..i-1], that are greater than v, to one position ahead
        while (j >= 0 && A[j] > v) {
            A[j + 1] = A[j]; // Move the larger element one position forward
            j--;             // Move the index to check the previous element
        }
        A[j + 1] = v; // Insert the element at the correct position
    }
}

```

- **Basic Operation** : Key Comparison , One per iteration `A[j] > v`
- **Show Two Loop Invariants** :
	- At every iteration the list is sorted prior to i . 
	- At every iteration the values after v are large .
- **Analysis** :
___
 Tags : #programming #algorithms 