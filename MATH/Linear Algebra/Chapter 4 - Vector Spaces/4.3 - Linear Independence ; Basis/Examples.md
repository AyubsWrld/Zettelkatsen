#### Example ( 1 ) 
____
> [!example] 
> **Let** $p_1(t) = 1 , p_2(t) = t , p_3(t) = 4 - t$ . Then ${p_1 , p_2 , p_2} is Linearly dependent in $P$ because $p_3 =4p_1 - p_2$  . 

This example exemplifies the notion that any set of vectors is linearly dependent if they can be expressed in a form $c_1 x_1 \ + \dots +c_n x_n = 0$   where $c_1 = c_2 = \dots = c_n$ . 

#### Example ( 2 ) 
____
Let $A$ be an invertible $n\times n$ matrix — say, $A = [a_1 , a_2 , \dots  , a_n]$ . Then the columns of A form a basis for $R^n$ because they are linearly independent and they span $R^n$ , by the Invertible Matrix Theorem.
#### Example ( 2 ) 
____
Let $A$ be an invertible $n\times n$ matrix — say, $A = [a_1 , a_2 , \dots  , a_n]$ . Then the columns of A form a basis for $R^n$ because they are linearly independent and they span $R^n$ , by the Invertible Matrix Theorem.

#### Example ( 3 ) 
____
> [!example] 
> $\mathbf{e}_1 = \begin{bmatrix} 1 \\ 0 \\ \vdots \\ 0 \end{bmatrix}, \quad \mathbf{e}_2 = \begin{bmatrix} 0 \\ 1 \\ \vdots \\ 0 \end{bmatrix}, \quad \dots, \quad \mathbf{e}_n = \begin{bmatrix} 0 \\ \vdots \\ 0 \\ 1 \end{bmatrix}$
This set spans $R^n$ and is referred to as the standard basis 

#### Example ( 4 ) 
____
> [!example] 
> *Let* $\mathbf{v}_1 = \begin{bmatrix} 3 \ 0 \ -6 \end{bmatrix}, \quad \mathbf{v}_2 = \begin{bmatrix} -4 \ 1 \ 7 \end{bmatrix}, \quad \text{and} \quad \mathbf{v}_3 = \begin{bmatrix} -2 \ 1 \ 5 \end{bmatrix}.$ Determine if ${\mathbf{v}_1, \mathbf{v}_2, \mathbf{v}_3} \text{ is a basis for } \mathbb{R}^3.$ 

We can either check if the the matrix is invertible . Row reduce and check if there exists any values within the null space .

$\begin{bmatrix}3 & 0 & -6 \\ -4 & 1 & 7 \\ -2 & 1 & 5 \end{bmatrix}$

#### Example ( 5 ) 
____
Find a basis for Col B, where
$B = [\mathbf{b}_1 \quad \mathbf{b}_2 \quad \cdots \quad \mathbf{b}_5] = \begin{bmatrix} 1 & 4 & 0 & 2 & 0 \\ 0 & 0 & 1 & -1 & 0 \\ 0 & 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 & 0 \end{bmatrix}$
Each nonpivot column of $B$ is a linear combination of the pivot columns. In fact, $\mathbf{b}_2 = 4\mathbf{b}_1$ and $\mathbf{b}_4 = 2\mathbf{b}_1 - \mathbf{b}_3$. By the Spanning Set Theorem, we may discard $\mathbf{b}_2$ and $\mathbf{b}_4$, and ${\mathbf{b}_1, \mathbf{b}_3, \mathbf{b}_5}$ will still span Col $B$. 

> [!note] 
> Looking at the matrix B, b₂ (the second column) is [4,0,0,0] and b₁ (the first column) is [1,0,0,0]. So b₂ = 4b₁ is correct because when you multiply b₁ by 4, you get b₂. If it were b₁ = 4b₂, that would mean multiplying [4,0,0,0] by 1/4 to get [1,0,0,0]. 

$$S = \left\{ b_1 , b_3 , b_5 \right\} = \left\{\begin{bmatrix}1 \\ 0 \\ 0 \\ 0 \end{bmatrix},\begin{bmatrix}0 \\ 1 \\ 0 \\ 0 \end{bmatrix},\begin{bmatrix}0 \\ 0 \\ 1 \\ 0 \end{bmatrix}\right\}$$ Since $\mathbf{b}_1 \neq \mathbf{0}$ and no vector in $S$ is a linear combination of the vectors that precede it, $S$ is linearly independent (Theorem 4). Thus $S$ is a basis for Col $B$.

...linear dependence relationship among the columns of $A$ can be expressed in the form $A\mathbf{x} = \mathbf{0}$, where $\mathbf{x}$ is a column of weights... However, the equations $A\mathbf{x} = \mathbf{0}$ and $B\mathbf{x} = \mathbf{0}$ have exactly the same set of solutions. If $A = [\mathbf{a}_1 \cdots \mathbf{a}_n]$ and $B = [\mathbf{b}_1 \cdots \mathbf{b}_n]$, then the vector equations

$x_1\mathbf{a}_1 + \cdots + x_n\mathbf{a}_n = \mathbf{0}$ and $x_1\mathbf{b}_1 + \cdots + x_n\mathbf{b}_n = \mathbf{0}$
