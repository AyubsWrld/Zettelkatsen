### 1. **Definition of a Vector Space**
   - A **vector space** is a set of vectors with two operations (addition and scalar multiplication) that satisfy the **ten axioms** (discussed earlier). A vector space must be **closed** under these two operations, meaning that:
     1. If $u$ and $v$ are in the vector space $V$, then $u + v$ must also be in $V$ (closure under addition).
     2. If $u$ is in $V$ and $c$ is a scalar, then $cu$ must also be in $V$ (closure under scalar multiplication).
### 2. **Subspaces**
   - A **subspace** is a subset of a vector space that is itself a vector space. In particular, a subspace must satisfy three conditions:
     1. It contains the **zero vector**.
     2. It is **closed under addition** (if $u, v \in H$, then $u + v \in H$).
     3. It is **closed under scalar multiplication** (if $u \in H$ and $c$ is a scalar, then $cu \in H$).

> [!important] 
> If any of these conditions fail, the set is not a subspace. 

### 3. **Geometric Interpretation**
   - The geometric interpretation of vector spaces (particularly in $\mathbb{R}^2$ and $\mathbb{R}^3$) is important for understanding closure under addition and scalar multiplication. For example, if a set consists of vectors from certain quadrants in the plane, you need to check if the operations result in vectors that remain in the same region.

> [!tip] 
> Draw the quadrants and try to see if you can produce an addition or scalar multiplicative which does not exist within those quadrants . 

### Key Axioms to Focus On:
   
1. **Closure under Addition**: This is important for checking whether the sum of two vectors remains in the set. Many of the practice problems ask you to verify whether the sum of vectors stays within the given set.

2. **Closure under Scalar Multiplication**: This checks if multiplying a vector by a scalar keeps the vector in the same set. If it fails, the set is not a vector space.

3. **Zero Vector**: The set must contain the zero vector (which is critical in subspace problems). If the zero vector is not included, the set is not a vector space or subspace.

### Applying the Theory to the Questions:

#### Problem 1: First Quadrant in the $xy$-Plane
You need to check if the first quadrant in the plane (where $x \geq 0$ and $y \geq 0$) satisfies the conditions for being a vector space.
- **Part a**: Is the set closed under addition? (Does $u + v$ remain in the first quadrant?)
- **Part b**: Is the set closed under scalar multiplication? (Can a scalar times a vector in the first quadrant still be in the first quadrant?)

#### Problem 2: Union of First and Third Quadrants
For this, the set consists of vectors from the first and third quadrants. You need to check:
- **Part a**: If a scalar times a vector in the set remains in the set (closure under scalar multiplication).
- **Part b**: Find examples where adding two vectors does not result in a vector that remains in the union of these quadrants (showing failure of closure under addition).

#### Problem 3: Unit Circle in the $xy$-Plane
The unit circle ($x^2 + y^2 \leq 1$) contains points inside and on the boundary of the unit circle. To show that this is not a subspace of $\mathbb{R}^2$, you need to find specific examples that violate one of the subspace conditions (either closure under addition or scalar multiplication).

#### Problem 4: Line in $\mathbb{R}^2$ Not Passing Through the Origin
This problem asks you to understand why a line that does not pass through the origin fails to be a subspace. The key observation is that it does not contain the zero vector (a necessary condition for subspaces).

#### Problems 5–8: Polynomial Subspaces
For these problems, you need to recall what a subspace of a polynomial space $P_n$ looks like. Key conditions to check:
1. **All polynomials of the form $p(t) = at^2$**: Check if this set is closed under addition and scalar multiplication.
2. **All polynomials of the form $p(t) = a + t^2$**: Similar checks as above.
3. **All polynomials with integer coefficients**: Are they closed under the necessary operations?
4. **Polynomials where $p(0) = 0$**: Check for closure and the zero polynomial.

### Strategy for Solving the Problems:
- For each problem, check whether the set satisfies the vector space axioms:
  1. Is the set **closed under addition**? (Test by adding vectors and verifying that the result is still in the set.)
  2. Is the set **closed under scalar multiplication**? (Multiply vectors by scalars and verify that the result stays in the set.)
  3. Does the set contain the **zero vector**? (If it doesn't, it's not a subspace.)

Understanding these core concepts will allow you to tackle each problem and identify whether the given sets are vector spaces or subspaces.