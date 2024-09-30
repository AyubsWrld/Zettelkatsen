#### Analysis of Algorithms
____
The analysis of algorithms involves evaluating their performance based on several key issues . 
1. **Correctness** : Ensures the algorithm produces the correct result for all possible inputs 
2. **Time Efficiency** : How long does it take for the algorithm to produce the correct output with respect to its input size . 
3. **Space Efficiency** : How much memory does the algorithm require ? 
4. **Optimality** : Determines whether the algorithm is the most efficient in terms of time or space for a given problem 
In short , we want the most correct , time and space efficient algorithm possible . So we worry about correctness first and then optimization .  

Lets turn to time Efficiency for a second . When we worry ourselves with time efficiency we wish to understand how long the algorithm takes to execute a basic unit of function with respect to the amount of inputs there are . 

- **Input Size** : The amount of data which is being processed by the algorithm 
- **Basic Operation** : The operation that has the most impact on the running time, typically something like comparisons or multiplication .  Think of this as the algorithms main tool for carrying out the job . 

This **Time Efficiency** is expressed as $T(n) \approx cop \cdot C(n)$ where $\dots$ 
- $cop$ is the execution time of the basic operation 
- $C(n)$ is the number of times the basic operation is performed 

### Input Size and Basic Operations (Examples)

| Problem                                     | Input Size Measure       | Basic Operation                      |
| ------------------------------------------- | ------------------------ | ------------------------------------ |
| Search for a key in a list of \( n \) items | Number of items \( n \)  | Key comparison                       |
| Multiply two matrices                       | Matrix dimensions        | Floating-point multiplication        |
| Polynomial evaluation                       | Degree of the polynomial | Floating-point multiplication        |
| Graph traversal                             | Number of vertices/edges | Visiting a vertex/traversing an edge |
| Number factorization                        | Number of bits           | Division                             |

---

### Cases of Time Complexity

Algorithms can exhibit different time complexities depending on the input:

- **Worst Case (\( W(n) \))**: The maximum time an algorithm takes over all inputs of size \( n \).
- **Best Case (\( B(n) \))**: The minimum time for all inputs of size \( n \).
- **Average Case (\( A(n) \))**: The expected time for a "typical" input, considering the probability distribution of the inputs.

For some algorithms, the average case is calculated as the expected number of repetitions of the basic operation, not merely the average of the best and worst cases.

### Amortized Efficiency

Amortized efficiency applies to a sequence of operations on the same data structure, spreading the cost of operations over multiple actions to give an average time per operation that is lower than the worst-case time.



 ___ 
 Tags : #programming #algorithms 