The **Johnson-Trotter algorithm** is a classical algorithm used to generate all permutations of a set of elements in a specific sequence known as "adjacent transpositions" or "neighbor swaps." In this context, adjacent transpositions mean that each permutation differs from the previous one by swapping only two adjacent elements.

### **Psuedocode**
1. Initialize: 
    - Create the first permutation in lexicographic order (1, 2, 3, ..., n)
    - Set the direction of all elements to LEFT (←)

2. Repeat the following until no mobile element is found:
    2.1. Find the largest mobile element:
        - A mobile element is one that is larger than the adjacent element in its current direction.
        - If the current direction is LEFT (←), check the element to the left.
        - If the current direction is RIGHT (→), check the element to the right.
        - Among all mobile elements, pick the largest one.

    2.2. Swap the largest mobile element with the adjacent element in the direction it's moving.

    2.3. Reverse the direction of all elements that are larger than the element just moved.

3. Terminate when no mobile element exists.

### **Key Characteristics**
- **Generates permutations by adjacent transpositions**: Every two consecutive permutations in the sequence are obtained by swapping two adjacent elements.
- **Efficiency**: The algorithm generates each new permutation in \( O(n) \) time, where \( n \) is the number of elements in the set.
- **No redundant permutations**: Each permutation appears exactly once.
  
### **Algorithm Overview**

The Johnson-Trotter algorithm uses two key concepts:
1. **Permutation direction (or "mobile" elements)**: Each element has a direction, either left (←) or right (→). Initially, all elements are set to move left.
2. **Largest mobile element**: An element is called "mobile" if it is larger than its adjacent element in the direction it is moving. At each step, the algorithm identifies the largest mobile element and swaps it with its adjacent element in the direction it is moving.

### **Steps of the Algorithm**
1. **Initialize**: Begin with the first permutation in lexicographic order. Assign a direction (usually left, ←) to all elements.
   
2. **Find the largest mobile element**: Identify the largest element that is "mobile" (i.e., has not reached the boundary of the permutation and is larger than the element it points to).

3. **Swap**: Swap the largest mobile element with the adjacent element in its current direction.

4. **Reverse directions**: After swapping, reverse the direction of all elements that are larger than the element just moved.

5. **Repeat**: Continue until there are no mobile elements remaining.

### **Example**

Let’s generate permutations for a set of three elements: \( \{1, 2, 3\} \).

1. **Initialization**: Start with \( \{1, 2, 3\} \), and all elements have a direction pointing left (←).

```
Permutation: 1  2  3
Directions:  ←  ←  ←
```

2. **Find the largest mobile element**: Initially, the largest mobile element is 3 (since it is the largest and moving left). Swap 3 with 2.

```
Permutation: 1  3  2
Directions:  ←  ←  ←
```

3. **Reverse directions of larger elements**: In this case, only element 3 moved, and there are no elements larger than 3, so no directions are changed.

4. **Next step**: Find the largest mobile element again. This time, the largest mobile element is 3, which is still moving left. Swap 3 with 1.

```
Permutation: 3  1  2
Directions:  ←  ←  ←
```

5. **Reverse directions**: After the swap, reverse the direction of all elements larger than 3 (there are none in this case).

6. **Continue**: Repeat this process until all permutations have been generated.

The complete sequence of permutations for this example would be:
1. \( \{1, 2, 3\} \)
2. \( \{1, 3, 2\} \)
3. \( \{3, 1, 2\} \)
4. \( \{3, 2, 1\} \)
5. \( \{2, 3, 1\} \)
6. \( \{2, 1, 3\} \)

### **Efficiency and Use**
- **Efficiency**: Each new permutation is produced in \( O(n) \) time by making a constant number of swaps and comparisons.
- **Use Cases**: The Johnson-Trotter algorithm is useful in applications where it is necessary to generate permutations of a set in an orderly manner, especially in problems that require generating permutations one at a time with minimal changes between consecutive permutations (e.g., puzzle-solving, generating all possible states in state-space search).

### **Final Notes**
- After generating the last permutation in lexicographic order, all elements have stopped moving, and the process terminates.
- The algorithm can be generalized to generate permutations of sets with repeated elements or applied to other combinatorial objects.

 ___
 Tags : #programming #algorithms 