### What is a Recurrence Relation?

A **recurrence relation** is a mathematical formula that defines a sequence of values based on previous terms in the sequence. It is often used in dynamic programming and other areas of computer science to express the solution to a problem in terms of smaller subproblems.

#### General Form:

A recurrence relation specifies:

- **Base cases**: These are explicitly defined values for the smallest subproblems, providing the starting point.
- **Recursive formula**: This defines how to compute the value of the function for a given problem size based on previously computed values.

---

### Example: Wall Building Problem

Let's revisit the recurrence relation for the wall problem:

- **Problem**: You want to build a wall of length `N` using the minimum number of bricks from a set of available brick lengths `L = {l₁, l₂, ..., lₘ}`.

#### Recurrence Relation:

1. **Base case**:
    
    f(0)=0f(0) = 0
    
    Building a wall of length `0` requires `0` bricks.
    
2. **Recursive case**: For `x > 0`:
    
    f(x)=min⁡{f(x−li)+1∣li≤x for all i}f(x) = \min \{ f(x - l_i) + 1 \mid l_i \leq x \text{ for all } i \}
    
    This states:
    
    - To determine the minimum number of bricks needed for a wall of length `x`, consider all possible bricks `l_i` that fit into the wall.
    - Use one brick of length `l_i` and solve the smaller subproblem of length `x - l_i`.
    - Add 1 to account for the brick `l_i` just used.
    - Take the minimum value across all choices of `l_i`.
3. **Invalid case**: If `x < 0`, no valid solution exists:
    
    f(x)=∞f(x) = \infty

---

### Understanding Through the Coin Change Analogy

The recurrence is similar to the **coin change problem**, where:

- Instead of brick lengths, you have coin denominations.
- Instead of building a wall, you are making a specific amount using the minimum number of coins.

For coin change, the recurrence relation is:

f(x)=min⁡{f(x−ci)+1∣ci≤x}f(x) = \min \{ f(x - c_i) + 1 \mid c_i \leq x \}

Where `c_i` represents the coin denominations.

---

### Why Are Recurrence Relations Useful?

1. **Modeling Problems**:
    
    - Recurrence relations help express complex problems in terms of simpler, overlapping subproblems.
    - They define how the solution to the current problem builds on the solutions to smaller problems.
2. **Dynamic Programming**:
    
    - A recurrence relation is central to dynamic programming.
    - It allows you to solve problems efficiently by storing the results of subproblems (in a table or memoization).
3. **Algorithm Efficiency**:
    
    - Recurrence relations lead to efficient algorithms by avoiding redundant calculations.

Would you like a further explanation or more examples?
___
 Tags : #programming #algorithms 