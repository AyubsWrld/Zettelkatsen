Asymptotic notations help analyze the efficiency of algorithms by focusing on the order of growth of their basic operation count. The three main notations used are Big-O, Big-Omega, and Big-Theta.

### Informal Introduction
Let $$t(n)$$ represent an algorithm's running time (basic operation count), and $$g(n)$$ represent a simple function to compare it with.

1. **Big-O notation** $$O(g(n))$$: The set of all functions with a lower or same order of growth as $$g(n)$$.
   - Examples:
     - $$n \in O(n^2)$$
     - $$100n + 5 \in O(n^2)$$
     - $$\frac{1}{2}n(n - 1) \in O(n^2)$$

2. **Big-Omega notation** $$\Omega(g(n))$$: The set of all functions with a higher or same order of growth as $$g(n)$$.
   - Examples:
     - $$n^3 \in \Omega(n^2)$$
     - $$\frac{1}{2}n(n - 1) \in \Omega(n^2)$$

3. **Big-Theta notation** $$\Theta(g(n))$$: The set of all functions with the same order of growth as $$g(n)$$.
   - Examples:
     - $$an^2 + bn + c \in \Theta(n^2)$$
     - $$n^2 + \sin(n) \in \Theta(n^2)$$

### Formal Definitions

- **O-notation**:
  $$ t(n) \in O(g(n)) $$ if $$ t(n) \leq c \cdot g(n) $$ for all $$ n \geq n_0 $$, where $$c$$ is a constant and $$n_0$$ is a nonnegative integer.

- **Omega-notation**:
  $$ t(n) \in \Omega(g(n)) $$ if $$ t(n) \geq c \cdot g(n) $$ for all $$ n \geq n_0 $$, where $$c$$ is a constant and $$n_0$$ is a nonnegative integer.

- **Theta-notation**:
  $$ t(n) \in \Theta(g(n)) $$ if $$ c_2 \cdot g(n) \leq t(n) \leq c_1 \cdot g(n) $$ for all $$ n \geq n_0 $$, where $$c_1$$ and $$c_2$$ are constants and $$n_0$$ is a nonnegative integer.

### Using Limits for Comparing Orders of Growth

To compare the order of growth of two functions $$ t(n) $$ and $$ g(n) $$, compute:

$$ \lim_{{n \to \infty}} \frac{t(n)}{g(n)} = \begin{cases} 
0 & \text{if} \, t(n) \, \text{has a smaller order of growth} \\
c & \text{if} \, t(n) \, \text{has the same order of growth} \\
\infty & \text{if} \, t(n) \, \text{has a larger order of growth}
\end{cases} $$

### Examples

1. Compare the growth of $$\frac{1}{2}n(n - 1)$$ and $$n^2$$:
   $$ \lim_{{n \to \infty}} \frac{\frac{1}{2}n(n - 1)}{n^2} = \frac{1}{2} \lim_{{n \to \infty}} \left( 1 - \frac{1}{n} \right) = \frac{1}{2} $$

   Therefore, $$\frac{1}{2}n(n - 1) \in \Theta(n^2)$$.

2. Compare $$ \log_2 n $$ and $$ \sqrt{n} $$:
   $$ \lim_{{n \to \infty}} \frac{\log_2 n}{\sqrt{n}} = 0 $$

   Therefore, $$ \log_2 n \in O(\sqrt{n}) $$.

 
 ___ 
 Tags : #programming #algorithms 