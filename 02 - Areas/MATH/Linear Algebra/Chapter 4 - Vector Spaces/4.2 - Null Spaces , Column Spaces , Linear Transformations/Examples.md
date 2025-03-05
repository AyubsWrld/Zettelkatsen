
#### Example 1 
____

> [!example] 
> *Example (l) : Let A be the matrix in (2) above, and let u = $\begin{bmatrix} 5 \\ 3  \\-2\end{bmatrix}$ . Determine if $u$ belongs to the null space of $A$ , Where $A= \begin{bmatrix} 1 & -3 & -2 \\ -5 & 9 & 1\end{bmatrix}$ .

> Simply Multiply $Au$ and see if is equivalent to $\begin{bmatrix} 0 \\ 0 \end{bmatrix}$  

> [!important] 
>   The reason this works is mainly because of **Theorem (2)** which states given $m\times n$  Matrix $A$ , any vector which when multiplied by $A$ gives us the zero vector is within Then null space of $A$ , denoted $Nul$ $A$  . 

___

#### Example 2 
____
> [!example] 
> *Example (ll) : $Nul \ A$ is a subset of $R^n$ because $A$ has $n$ Columns.  It follows that any vector within the $Nul$ space of $A$ can be multiplied and added to produce another value which is also within the $Nul$ space of $A$ * 

#### Example 3 
____

> [!example] 
> *Example (lll) : Let H be the set of all vectors in $R^4$ whose coordinates a , b , c , d satisfy the equations $a -2b+5c=d$  and $c - a = b$ . Show that H is a subspace of $R^4$  .*

With this we simply wish to show that $H$ is equivalent to the Zero vector therefore anything which is multiplied by this Matrix is also the Zero vector  

> 1. *Move all the values to the left*
> $$a - 2b + 5c - d = 0$$$$-a -b + c = 0$$ 

> [!missing] 
> Explain this further why does it make sense ? 

___

#### Example 4 
____
> [!example] 
> *Example (IV) : Find the spanning set for the null space of the matrix* $$A=\begin{bmatrix} -3 & 6 &-1&1&-7\\1&-2&2&3&-1\\2&-4&5&8&-4\end{bmatrix}$$ 


> [!tip] 
> **Basic Variables** : Variables which serve as pivot points . in this case $x_1$ and $x_2$ . 
> **Free Variables** : Variables which do not serve as pivot points . in this case $x_2$ and $x_4$ and $x_5$ . 
>  

Here we are asked to produce the spanning set for the matrixes . 

1. Find the general solution of $Ax = 0$ in terms of free variables  . 
	1. Row reduce the augmented matrix $[A 0]$ to reduced echelon form in order to write the basic variables in terms of the free variables . $$A=\begin{bmatrix} 1 & -2 &0&-1&3&0\\0&0&1&2&-2&0\\0&0&0&0&0&0\end{bmatrix}$$
	2. Write the basic variables in terms of the free variables 
	3. The general solution is..
		1. $x_1$ = $2x_2 + x_4  - 3x_5$ 
		2. $x_3$ = $-2x_4  + 2x_5$
	4. Decompose the vector giving the general solution into a linear combination of vectors where the weights are the free variables. that is 
$$
\begin{bmatrix}
x_1 \\
x_2 \\
x_3 \\
x_4 \\
x_5
\end{bmatrix}
=
\begin{bmatrix}
2x_2 + x_4 - 3x_5 \\
x_2 \\
-2x_4 + 2x_5 \\
x_4 \\
x_5
\end{bmatrix}
=
x_2
\begin{bmatrix}
2 \\
1 \\
0 \\
0 \\
0
\end{bmatrix}
+
x_4
\begin{bmatrix}
1 \\
0 \\
-2 \\
1 \\
0
\end{bmatrix}
+
x_5
\begin{bmatrix}
-3 \\
0 \\
2 \\
0 \\
1
\end{bmatrix}
$$
Every linear combination of $x_2$ , $x_4$ , and $x_5$ is an element of $Nul\ A$ and vice versa . Thus $\{x_1 , x_2 , x_3\}$  is a spanning set for $Nul\ A$ . 


#### Example 4 ( Practice Problems ) 
____
1. find an explicit description of Nul A by listing vectors that span the null space. We want to find a basis ( linearly independent set of vectors ) which describes the null space of A 
	1. **Let** $A = \begin{bmatrix} 1 & 3 & 5 & 0 \\ 0 & 1 & 4 & -2 \end{bmatrix}$
		1. Reduce to **RREF** : $A = \begin{bmatrix} 1 & 0 & -7 & 6 \\ 0 & 1 & 4 &  -2 \end{bmatrix}$
		2. identify free variables : $x_3 , x_4$ are free variables  . If there were any pivots they would also be free variables
		3. Put it in [[General Solution]] with free variables as weights .  $x_1 = 7x_3 - 6x_4$ , $x_2 =  -4x_3 +2x_4$
		4. Place in vector form : $x_3\begin{bmatrix} 7 \\ -4 \\ 1 \\ 0 \end{bmatrix} , x_4\begin{bmatrix} -6 \\ 2 \\ 0 \\ 1 \end{bmatrix}$ 
____

### Example (5)  : Column Space
____
> [!example] 
> *Find Matrix A such that W = $Col \  A$* 
>	${W = \left\{\begin{bmatrix} 6a-b \\ a+b \\ -7a \end{bmatrix} : a,b \text{ in } \mathbb{R}\right\}}$
*Solution* : First we write $W$ as a set of linear combinations. 
>	${W = \left\{a\begin{bmatrix} 6 \\ 1 \\ -7 \end{bmatrix} b\begin{bmatrix} -1 \\ 1 \\ 0 \end{bmatrix}: a,b \text{ in } \mathbb{R}\right\}}$  = $\text{ Span = }\left\{\begin{bmatrix} 6 \\ 1 \\ -7 \end{bmatrix}, \begin{bmatrix} -1 \\ 1 \\ 0 \end{bmatrix} \right\}$ 
*Use the vectors in the spanning set as columns for the Matrix*
>	$A = \begin{bmatrix} 6 & -1 \\ 1  & 1 \\ -7 & 0 \end{bmatrix}$ 

> [!note] 
> The column space of an $m\times n$ matrix A is all of $R^m$ if and only if the equation $Ax = b$ has a solution for each b in $R^m$ . This essentially means that the subspace of a is equivalent to the entirety of $R^m$ if for every vector in $R^m$ we can reach it using the column space . 

### Example (6)  : Column Space
____
> [!example] 
> *Let* $A = \begin{bmatrix} 2 & 4 & -2 & 1 \\ -2 & -5 & 7 & 3 \\ 3 & 7 & -8  & 6 \end{bmatrix}$
a. If the column space of $A$ is a subspace of $R^k$ , what is $k$ ? 
	Guess : Since a subspace is a set of vectors which are closed under linear operations  in $dim \leq$ $k$  . And the column space of $A$ is in itself of a subset of $R^m$ . 
	Answer : The columns of A each have three entries, so Col A is a subspace of $R^k$ , where $k = 3$
	b. If the null space of A is a subspace of $R^k$ , what is $k$?
	Answer: A vector $x$ such that $Ax$ is defined must have four entries, so $Nul \ A$ is a subspace of $R^k$ , where $k = 4$ 


### Example (7)  : Finding Values
____
> [!example] 
> With A as in Example 5, find a nonzero vector in Col A and a nonzero vector in Nul A.
> 1. Finding a non-zero vector in $Col(A)$ is simple just list any column . 
> 2. Finding a non-zero vector in $Nul(A)$ is a bit harder . As we need to find a spanning set of vectors for all the vectors within $Nul(A)$

#### Example (8) 
---
> [!example] 
> With $A$ and $\mathbf{u} = \begin{bmatrix} 3 \\ -2 \\ -1 \\ 0 \end{bmatrix} \text{ and } \mathbf{v} = \begin{bmatrix} 3 \\ -1 \\ 3 \end{bmatrix}$
> Determine if u is in Nul A. Could u be in Col A? and Determine if v is in Col A. Could v be in Nul A

1. $u$ can be in Nul A if $Au = 0$ so that means if we multiply $u$ by $A$ we will get the zero vector . 
	1. $\begin{bmatrix} 2 & 4 & -2 & 1 \\ -2 & -5 & 7 & 3 \\ 3 & 7 & -8  & 6 \end{bmatrix}\cdot \begin{bmatrix} 3 \\ -2 \\ -1 \\ 0 \end{bmatrix}$  = $\begin{bmatrix} 0 \\ 0 \\ 0 \\ 0 \end{bmatrix}$ 


---
Tags : #math #linear-algebra