A **loop invariant** is a condition or property that remains true before and after each iteration of a loop during the execution of an algorithm. It is used to reason about the correctness of algorithms, particularly those involving loops. By demonstrating that the invariant holds:

1. **Before the loop starts** (initialization),
2. **At the beginning of each iteration**, and
3. **After the loop ends** (termination),

you can prove that the algorithm is correct.

### Components of Loop Invariant:

1. **Initialization**: The invariant should be true before the first iteration of the loop.
2. **Maintenance**: The invariant should remain true after each iteration of the loop.
3. **Termination**: When the loop terminates, the invariant, combined with the loop's exit condition, should imply the correctness of the result.

### Example: Loop Invariant in Insertion Sort

In the **Insertion Sort** algorithm, we can define a loop invariant to prove its correctness.

```cpp
for (int i = 1; i < n; i++) {
    int key = arr[i];
    int j = i - 1;
    while (j >= 0 && arr[j] > key) {
        arr[j + 1] = arr[j];
        j = j - 1;
    }
    arr[j + 1] = key;
}
```

#### Loop Invariant for Insertion Sort:
At the start of each iteration of the outer loop (for `i = 1` to `n`), the subarray `arr[0...i-1]` is sorted.

- **Initialization**: Before the first iteration (`i = 1`), the subarray `arr[0...0]` contains just one element, which is trivially sorted.
- **Maintenance**: During each iteration, the algorithm inserts `arr[i]` into its correct position in the sorted subarray `arr[0...i-1]`, so that `arr[0...i]` is sorted.
- **Termination**: When the loop terminates at `i = n`, the invariant guarantees that the entire array `arr[0...n-1]` is sorted.

### Purpose of Loop Invariants:
- **Correctness Proof**: They help formally prove that an algorithm behaves as expected.
- **Understanding Behavior**: Loop invariants also give insights into the intermediate state of the algorithm and how the solution progresses.

In summary, a loop invariant is a powerful tool in algorithm analysis and helps verify the correctness and efficiency of algorithms involving loops.
 ___ 
 Tags : #programming #algorithms 