### Dynamical Systems 
___
> [!example] (1)
>  $x = \begin{bmatrix} 2 & 4 \\ -2 & 6 \end{bmatrix} , \ x(0) = \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$ 

  ![[Pasted image 20241208213241.png]]
![[Pasted image 20241208213326.png]]


### Euclidean Real Spaces
___
Space $V$ is called a space with inner product ( Euclidean ) if for all $\vec{a} , \ \vec{b}$   from $V$ we can define the numbers $<\vec{a} , \vec{b}>$  ( or $\vec{a} \cdot \vec{b}$ ) . This just follows similar constraints of a regular vector space ,Transitivity and scalar multiplication and addition . Also ... 

![[Pasted image 20241208214038.png]]

Distance b , a = b - a .

a and b are called orthogonal if $< a , b >$ = 0

$\bar{a} = \dfrac{<a ,b>}{b^2}b$ is called the orthogonal projection of $\vec{a}$ onto $\vec{b}$ . 

![[Pasted image 20241208214343.png]]


Orthogonal Compliment = $\vec{a}^{\perp} = a -\vec{Proj_b a}$  .


Triangle Inequality : $|| a + b|| \leq ||a|| + ||b||$ 

Crone Theorem $||a+b|| = ||a||^2 + ||b||^2 - 2<a,b>$

if $a , \ b$ are orthogonal then $||a+b|| = ||a||^2 + ||b||^2$ 


### Orthogonal Basis
---
A set of nonzero mutually orthogonal vectors is linearly independent ( Zero is orthogonal to every vector so we don't include it ) . it follows that A set of n mutually orthogonal vectors constitute a basis in an n-dimensional space . 


### Gram Schmidt Procedure 
---
Given a set of vectors in an n-dimensional space . the `Gram Schmidt` procedure takes these vectors and forms a new set orthogonal basis vectors. 

The steps are as follows ... 
1. Set new vector $\vec{u}_1$ = to the original basis vector $\vec{v}_1$ .
2. For the second vector $\vec{u}_2$ , set it equal to $\vec{v}_2$ - $\dfrac{<v_2 , u_1>}{||\vec{u_1}||^2} \vec{u}_1$ 
3. $u_3 = v_3 - \frac{\langle v_3, u_1\rangle}{\langle u_1, u_1\rangle} u_1 - \frac{\langle v_3, u_2\rangle}{\langle u_2, u_2\rangle} u_2$

The pattern is simply for each new vector we must subtract an additional term with an inner product between the current v vector and a previous u vector . 
![[Pasted image 20241208221515.png]]

$\forall \ m\times n \ matrix \  A , (Row A)^\perp$   =  Null A . Ax = 0 for each $\vec{r}_i$ is orthogonal to every $\vec{x} \in \text{Null A}$ . dim(Null A) + dim(Row A ) = n . And $\text{Null A} + \text{Row A} = R^n$ . 


____

Tags : #math #linear-algebra