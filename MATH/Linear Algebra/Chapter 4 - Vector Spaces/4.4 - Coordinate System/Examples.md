#### Example (1) 
___
> [!example] 
> Consider a basis $B = \{b_1, b_2\}$ for $\mathbb{R}^2$, where $b_1 = \begin{bmatrix} 1 \\ 0 \end{bmatrix}$ and $b_2 = \begin{bmatrix} 1 \\ 2 \end{bmatrix}$. Suppose an x in $\mathbb{R}^2$ has the coordinate vector $[x]_B = \begin{bmatrix} -2 \\ 3 \end{bmatrix}$. Find x. 

#### Example (2) 
___
> [!example] 
> The entries in the vector $x$ = $\begin{bmatrix} 1 \\ 6 \end{bmatrix}$ are the coordinates of $x$ relative to the *standard basis* since the *Standard Basis* = $\mathbb{E} = \{ e_1 , e_2 , ... , e_n\}$  . And $\begin{bmatrix} 1 \\ 6 \end{bmatrix}$  is equivalent to $1 \cdot \begin{bmatrix} 1 \\ 0 \end{bmatrix}$ + $6 \cdot \begin{bmatrix} 0 \\ 1 \end{bmatrix}$ . 

#### Example (3) 
___
> [!example] 
> Let $b_1$ = $\begin{bmatrix} 2 \\ 1 \end{bmatrix}$ , $b_2$ = $\begin{bmatrix} -1 \\ 1 \end{bmatrix}$, $x$ = $\begin{bmatrix} 4 \\ 5 \end{bmatrix}$   , and $\mathbb{B} = \{ b_1 , b_2\}$ , find the *coordinate vector* $[x]_{\mathbb{b}}$ of $x$ relative to $\mathbb{B}$  .  

This example we are given the a basis in $R^2$ ( A set of linearly independent vectors which span the entirety of the space ) . And we are given a value $x$ *coordinate vector* (  a vector in terms of a specific basis ) . So we are essentially looking for $x$ expressed using the basis $\mathbb{B}$ . 

$c_1 \begin{bmatrix} 2 \\ 1 \end{bmatrix}$  + $c_2 \begin{bmatrix} -1 \\ 1\end{bmatrix}$ = $\begin{bmatrix} 4 \\ 5 \end{bmatrix}$   

Which is equivalent to ... 

$\begin{bmatrix} 2 &  -1 \\ 1 & 1 \end{bmatrix}$ $\begin{bmatrix} c_1 \\ c_2 \end{bmatrix}$  = $\begin{bmatrix} 4 \\ 5 \end{bmatrix}$  

Which we can solve using a system of linear equations . 

#### Example (5)
___
> [!example] 
> Use coordinate vectors to verify that the polynomials $1 + 2t^2$, $4 + t + 5t^2$, and $3 + 2t$ are linearly dependent in $\mathbb{P}_2$. 

Solution The coordinate mapping produces the coordinate vectors $(1,0,2)$, $(4,1,5)$, and $(3,2,0)$, respectively. Writing these vectors as the columns of a matrix $A$, we can determine their independence by row reducing the augmented matrix for $Ax = 0$:

$$\begin{bmatrix}
1 & 4 & 3 & 0 \\
0 & 1 & 2 & 0 \\
2 & 5 & 0 & 0
\end{bmatrix} \sim 
\begin{bmatrix}
1 & 4 & 3 & 0 \\
0 & 1 & 2 & 0 \\
0 & 0 & 0 & 0
\end{bmatrix}
$$

#### Example (6)
___
> [!example] 
> Let
$$
\mathbf{v}_1 = \begin{bmatrix} 3 \\ 6 \\ 2 \end{bmatrix}, 
\mathbf{v}_2 = \begin{bmatrix} -1 \\ 0 \\ 1 \end{bmatrix}, 
\mathbf{x} = \begin{bmatrix} 3 \\ 12 \\ 7 \end{bmatrix},
$$

> [!example] 
> and $B = \{\mathbf{v}_1, \mathbf{v}_2\}$. Then $B$ is a basis for $H = \text{Span}\{\mathbf{v}_1, \mathbf{v}_2\}$. Determine if $\mathbf{x}$ is in $H$, and if it is, find the coordinate vector of $\mathbf{x}$ relative to $B$. 
	


