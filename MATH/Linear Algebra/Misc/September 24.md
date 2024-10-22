Dimension of a space
Plane of vectors there exists two lin independent vectors any set of 3 [[colinear vectors ]] , can be expressed as a linear combination of two vectors 

$a = x_1u + x_2v$ 
$x_1u + x_2v + (-1a) = 0$ 
hence $u,v,a$ are [[Linearly Independent]] . opposite of [[Linearly Dependent]]

If $u,v$ are colinear then $u = \lambda v$

A plane is a two dimensional [[MATH/Linear Algebra/Misc/Vector Spaces/4.1/Vector Space]]

#### _Theorem_ $R^2$ is 2 dimensional 
___
$\exists$ 2 lin indep columns  , for instance 
$$ e_1 =
\begin{bmatrix} 
	0\\
	1\\
	\end{bmatrix}
$$

$$ e_2 =
\begin{bmatrix} 
	0\\
	0\\
	\end{bmatrix}
$$
Any three columns in $R^2$ are [[Linearly Independent]]

$$ a =
\begin{bmatrix} 
	a_\beta\\
	a_\alpha\\
	\end{bmatrix}
$$

$$ b =
\begin{bmatrix} 
	b_\alpha\\
	b_\beta\\
	\end{bmatrix}
$$
(I) $a_1$  , $a_2$ are not [[Proportional]] . Suppose 
$$ c =
\begin{bmatrix} 
	c_\alpha\\
	c_\beta\\
	\end{bmatrix}
$$
is some vectores , we can prove that $a_3$ = Linear combination of $a_1$ and $a_2$ 


given that $a,b$ are not [[Proportional]] then the [[Determinant]] of $a \ and\  b$ $\neq 0$
Then has a unique ______ 'idk' by [[Cramers Rule]] .  

(ii) If $a = xb$ , then $1 \times a  - xb + 0 \times c = 0$

All to say that if you have 2 linearly independent vectors , if you add a third the system will become linearly dependent . 

#### Properties of [[Linear dependence]]
____
> (P1) A set is linearly dependent $iff$ one of the vectors is a [[Linear Combination]] of the others . 
> (P2) A set that includes 0 is [[Linearly Dependent]] . 
> (P3) A set that includes a [[Linearly Dependent]] subset is [[Linearly Dependent]]

##### Def'n 
____
A set of $n$ [[Linearly Independent]] vectors in an [[n-dimenstion]] Space is called a [[Basis]] in the space . 
#####  Theorem
____
Every vector in a space of [[Linear Combination]] of Basis Vectors . This [[Linear Combination]] is unique  . 
(i) Let $E = \{e_1, e_2 , \dots , e_n\}$ is a basis in some `n-dimensional` space $V$ . Let $a$ be some vector from $V$ . we need to show that $V \in$  span $\{e_1,\dots,e_2\}$
>if a is one of $\{e_1,\dots,e_2\}$ for instance $a_1 = e_i$ then $a$ = $0\times \{e_1,\dots ,e_n\}$ 
>if a is not one of the basis vectors the the set is [[Linearly Dependent]] as a set of $(n+1)$ vectors then $\exists$ non-trivial [[Linear Combination]] equal to the [[Zero Vector]] 

If $x_{n+1} = 0$ and one of $x_1,\dots,x_n$ is non zero we get $x_1e_1, + x_n+e_n = 0$   nontrivial and must be [[Linearly Dependent]]  which cannot be true . Therefore , $x_n+1\neq 0$ then  

Suppose the linear comboination 2 is not unique then there is another [[Linear Combination]] , $a =\beta_1e_1 + \dots + \beta_ne_n$

##### Disproof 
____
$a - a = 0$ then $(\beta_1e_1 + \dots + \beta_ne_n$) - $(\lambda_1e_1+ \dots + \lambda_ne_n)$ = 0  since the set of vectors $E$ is [[Linearly Independent]] it can hold if 

[[Isomorphism]] . 


A polynomial is a set of coefficients  

[[Finite Dimensional Spaces]] 

Dimensional Space $V$ is the maximum number of [[Linearly Independent]] Vectors in a set . also dim$V$  =  $n$ the number of vectors in a [[Linearly Independent]] set called a basis 

#### Theorem
____
A [[Basis]] [[Span]]s the whole spae every vector e is unique of the vector space . 

#### Theorem
___
**A basis**
>(i) Spans the whole space 
>(ii) is [[Linearly Independent]] 

#### Theorem
___
A set of vectors fewer than n vectors does not span n-dimensional Space $V$ , 
Prove by contradiction that a set of vectors fewer than n vectors does span n-dimensional Space $V$ 


Every basis must contain the same number of vectors equal to the dimensional space 


### Subspaces 
___
##### Subspaces of vector spaces 
>A subset $S$ of vector space $V$ if it is a vector space itself , Not every subset of a Vector space is a subspace . 
>	Ex. $U =\{u,v,w\}$ because $2u+3v \notin U$  , no [[MATH/Linear Algebra/Misc/Review/Closure]] .
>	Ex. A set of all [[Unit Geometric Vectors]] is not a subspace  of the space of [[Geometric Vectors]] . $||u||=1 \ ,||v|| = 1 , ||a|| = 1$ , $||a+v|| \neq 1$ . 
>	Ex. The set of al polynomials of the type $p = a_0 +a_1t$ is a subspace of $P^2$ $q = b_0 + b_1t$ $\rightarrow$ $p+q$ $\in$ [[Linear Polynomials]] 


