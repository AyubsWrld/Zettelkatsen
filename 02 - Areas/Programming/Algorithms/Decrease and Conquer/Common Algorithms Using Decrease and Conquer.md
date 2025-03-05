#### **2.1 Insertion Sort**

- **Technique**: Decrease by a constant.
- **Procedure**: Insertion sort progressively sorts a portion of the list by taking one element and inserting it into the already sorted section. The algorithm ensures that at each iteration, a larger part of the list is sorted.

#### **2.2 Binary Search**

- **Technique**: Decrease by a constant factor.
- **Procedure**: The list is divided in half, and depending on the comparison, the algorithm continues searching in either the left or right half. It has a logarithmic time complexity, O(log⁡n)O(\log n)O(logn).

#### **2.3 Topological Sorting**

- **Technique**: Decrease by a constant.
- **Application**: Used on directed acyclic graphs (DAGs) to linearly order vertices such that for every directed edge u→vu \rightarrow vu→v, vertex uuu comes before vvv in the ordering.
- **Algorithm**: Typically implemented using depth-first search (DFS).

#### **2.4 Euclid’s Algorithm**

- **Technique**: Variable-size decrease.
- **Procedure**: The GCD of two numbers is found by successively replacing the larger number with its remainder when divided by the smaller number. The process is repeated until the remainder is zero.
 ___
 Tags : #programming #algorithms 
