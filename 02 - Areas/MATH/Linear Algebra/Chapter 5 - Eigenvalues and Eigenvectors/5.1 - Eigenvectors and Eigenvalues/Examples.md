
#### Example (1)
___
> [!example] 
> $Au = \begin{bmatrix} 1 & 6 \\ 5 & 2 \end{bmatrix}\begin{bmatrix} 6 \\ -5 \end{bmatrix} = \begin{bmatrix} -24 \\ 20 \end{bmatrix} = -4\begin{bmatrix} 6 \\ -5 \end{bmatrix} = -4u$
$Av = \begin{bmatrix} 1 & 6 \\ 5 & 2 \end{bmatrix}\begin{bmatrix} 3 \\ -2 \end{bmatrix} = \begin{bmatrix} -9 \\ 11 \end{bmatrix} \neq \lambda\begin{bmatrix} 3 \\ -2 \end{bmatrix}$ 

> [!quote] 
> Hypothesis : Essentially think of it can the resulting matrix under the transformation  $A$ be expressed in more simpler terms than the matrix . Does the Transformation simply just stretch the matrix ? 

> [!check] 
> The transformation retains the spanning vectors and simply multiplies the vectors by some scalar mutliple . 


#### Example (2)
___
> [!example] 
> Suppose $A = \begin{bmatrix} 1 & 6 \\ 5 & 2 \end{bmatrix}$ . Show that $7$ is an *eigenvalue* of matrix $A$ and find the corresponding *eigenvector* . 
> If $(A - \lambda I) = 0$ has a nontrivial solution then $\lambda$ is an eigenvalue 
> 

**Solution** : $7$ is an eigenvalue of $A$ if the equation $Ax = 7x$ has a non-trivial solution $Ax -7x = 0 or $(A-7 I) = 0$   ( Why ? ) . To solve this homogenous equation we can form the matrix $A - 7I = \begin{bmatrix} 1 & 6  \\ 5 & 2 \end{bmatrix} - \begin{bmatrix} 7 & 0 \\ 0 & 7 \end{bmatrix} = \begin{bmatrix} -6 & 6 \\ 5 & -5 \end{bmatrix}$    the rows are obviously linearly dependent so $A$ has a non-trivial solution therefore Thus $7$ is a eigenvalue . 

Now to find the corresponding eigenvectors  we use row operation and express the values in terms of a general solution . ( recall how we did it within calculating a general solution for the basis of a null space ) . 

$\begin{bmatrix} -6 &  6 &  0 \\  5 &  -5 & 0 \end{bmatrix}$ $\rightarrow \text{Row Operations} \rightarrow$  $\begin{bmatrix} 1 & -1 & 0 \\ 0 & 0 & 0 \end{bmatrix}$ , the general solution $x^2\begin{bmatrix}1 \\ 1 \end{bmatrix}$  . each vector of this form with $x^2 \neq 0$ is an eigenvector  corresponding to the $\lambda =7$ . 