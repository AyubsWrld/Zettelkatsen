
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
		4. Place in vector form 
____

Tags : #math #linear-algebra