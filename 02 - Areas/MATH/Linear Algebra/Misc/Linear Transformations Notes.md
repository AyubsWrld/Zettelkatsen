For $\forall v \in V$   assign $u = T(v)$ from $u$  . 
$u$ is unique for every $\vec{v}$  (A preimage of $\vec{u}$) the image of $\vec{v}$ . 
The set of all integers is called the image of $T$ . 
If range = codomain then $T$ is called onto (surjection) . 
If every $\vec{u}$  from the range has exactly one preimage then $T$ is called 1 to 1 map or an injection . 
$\vec{w} = T_2(\vec{u}) = T_2(T_1(\vec{v}))$
$\vec{v} = T_1(\vec{u}) = T_{-1}(T_1(\vec{v}))$

$T^{-1} \cdot T = I$ 
Kernel T = $\forall \vec{v} \in kerT$ , $T(\vec{v} = \vec{0})$

$T : V \rightarrow U ,  V , U$ are vector spaces is called linear if $\forall \  \vec{a} , \vec{b} from V$   
$T : V \rightarrow U ,  V , U$ are vector spaces is called linear if $\forall \  \vec{a} , \vec{b} from V$   
1. $T(\lambda \vec{a})$ = $\lambda T({a})$
1. $T(\lambda \vec{a} + \phi \vec{b})$ = $\lambda T(\vec{a}) + \phi T(\vec{b})$


Proposition 1. Every matrix transformation is linear . 

Can every linear transformation be presented as a matrix transformation ? 
Let $T : V \rightarrow U$ 

$T(\vec{e_1}) = \vec{u_1} = a_{11}\vec{b_1} +  a_{21}\vec{b_2} + ...+ a_{m1}\vec{b_m}$
$T(\vec{e_2}) = \vec{u_2} = a_{12}\vec{b_u} +  a_{22}\vec{b_2} + ...+ a_{m1}\vec{b_m}$
$T(\vec{e_n}) = \vec{u_n} = a_{1n}\vec{b_u} +  a_{2n}\vec{b_2} + ...+ a_{m1}\vec{b_m}$
$T(\vec{e_1}) = [\vec{b_1} , \vec{b_2} , \dots , \vec{b_m}]$ $\cdot$ 


Every matrix transformation from $R^n \ into \  R^m$ is linear $A \cdot (\vec{a} + \vec{b})$ = $A\vec{a} + A\vec{b}$
$$ m=
\begin{bmatrix} 
	0 & 1 & 1 \\
	1 & 0 & 1\\
	1 & 1 & 0 \\
	\end{bmatrix}
$$
Example : 

$T : R^3 \rightarrow R^2$

$$ t
\begin{bmatrix} 
	x_1 \\
	x_2 \\
	x_3 \\
	\end{bmatrix} = 
\begin{bmatrix} 
	x_1 - 2x_2 +x_3 \\
	-x_1 + x_2 +3x_3\\
	\end{bmatrix} 
$$ what is the domain ? codomain ? is t linear ? is t onto ? is t invertible ? 

Codomain = $R^3$ 
Codomain = $R^2$ 

Show that T is a matrix transformation  this will show it is linear 
$$ A = T
\begin{bmatrix} 
	1 \\
	0 \\
	0 \\
	\end{bmatrix} 
\begin{bmatrix} 
	0 \\
	1 \\
	0 \\
	\end{bmatrix} 
\begin{bmatrix} 
	0 \\
	0 \\
	1 \\
	\end{bmatrix} = 
	
\begin{bmatrix} 
	1 && -2 && 1\\
	-1 && 1 && 3\\
	\end{bmatrix}$$
	
$$ T
\begin{bmatrix} 
	x_1 \\
	x_2 \\
	x_3 \\
	\end{bmatrix} = 
\begin{bmatrix} 
	1 && -2 && 1 \\
	-1 && 1 && 3\\
	\end{bmatrix} 
	\cdot
\begin{bmatrix} 
	x_1 \\
	x_2 \\
	x_3 \\
	\end{bmatrix}$$
is it onto ? is there a preimage of $\begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix}$ for every $\begin{bmatrix} x \\ y \end{bmatrix} \in R^2$  
is it onto ? is $\begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix}$ unique for every image $\begin{bmatrix} x \\ y \end{bmatrix} \in R^2$   

There is a solution for every x , y however it is not unique : $x_3$ is a free variable therefore it is not a bijection and is therefore not isomorphic . through finding the general solution see screenshot . 

kernel of T is the null space of $A$  

$T(\vec{x})$ = $\vec{0}$ 
$kerT = {\vec{x} : T(\vec{x}) = \vec{0}}$ 
where $A\vec{x} = \vec{0}$ 

____

Tags : #math #linear-algebra