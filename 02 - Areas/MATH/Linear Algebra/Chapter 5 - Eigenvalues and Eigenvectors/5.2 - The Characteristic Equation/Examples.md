#### Example (1) 
___
> [!example] 
> Find the eigenvalues of $A = \begin{bmatrix} 2 & 3 \\ 3 & -6 \end{bmatrix}$ 

We must find all the scalars $\lambda$ such that $(Ax -\lambda x) = 0$

By the Invertible Matrix Theorem , this problem is equivalent to finding all $\lambda$ such that $A - \lambda I$ is not invertible . 

$A - \lambda I = \begin{bmatrix} 2 & 3 \\ 3 & -6 \end{bmatrix} - \begin{bmatrix} \lambda & 0 \\ 0 & \lambda \end{bmatrix}$  = $\begin{bmatrix} 2 - \lambda & 3 \\  3  & -6 - \lambda \end{bmatrix}$   . This matrix fails to be Invertible when its *Determinant* is zero . $$ \text{det}(A - \lambda I) \text{det} \begin{bmatrix} 2 - \lambda & 3 \\  3  & -6 - \lambda \end{bmatrix}$$ Recall that 

$\text{det} \begin{bmatrix} a & b \\ c &  d \end{bmatrix}$ = $ad - bc$  

so we arrive at 

$\det(A - \lambda I) = (2 - \lambda)(-6 - \lambda) - (3)(3)$
$= -12 + 6\lambda - 2\lambda + \lambda^2 - 9$
$= \lambda^2 + 4\lambda - 21$
$= (\lambda - 3)(\lambda + 7)$

We want the values of lambda which set the values to zero so , $\lambda_1 = 3 , \lambda_2 = -7$  . 

#### Example (2) 
___

> [!example] 
> Compute det $A$ for $A = \begin{bmatrix} 1 & 5 & 0 \\ 2 & 4 & -1 \\ 0 & -2 & 0 \end{bmatrix}$. 

SOLUTION :  The following row reduction uses one row interchange:

$A \sim \begin{bmatrix} 1 & 5 & 0 \\ 0 & -6 & -1 \\ 0 & -2 & 0 \end{bmatrix} \sim \begin{bmatrix} 1 & 5 & 0 \\ 0 & -2 & 0 \\ 0 & -6 & -1 \end{bmatrix} \sim \begin{bmatrix} 1 & 5 & 0 \\ 0 & -2 & 0 \\ 0 & 0 & -1 \end{bmatrix} = U_1$

So det $A$ equals $(-1)^1(1)(-2)(-1) = -2$. The following alternative row reduction avoids the row interchange and produces a different echelon form. The last step adds $-1/3$ times row 2 to row 3:

$A \sim \begin{bmatrix} 1 & 5 & 0 \\ 0 & -6 & -1 \\ 0 & -2 & 0 \end{bmatrix} \sim \begin{bmatrix} 1 & 5 & 0 \\ 0 & -6 & -1 \\ 0 & 0 & 1/3 \end{bmatrix} = U_2$

This time det $A$ is $(-1)^0(1)(-6)(1/3) = -2$, the same as before.