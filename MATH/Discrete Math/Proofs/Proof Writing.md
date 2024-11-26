## | Proving Statements with Contradiction
- Alongside our tool bag of possible solutions to prove whether a statement is true or false , we can prove statements by *contradiction* . This process essentially entails that given a statement we can negate the proposition and if we arrive at an impossibility it implies that the original statement was true .  ==A real number x is rational if x = a b for some a,b ∈ Z. Also, x is irrational if it is not rational, that is if x 6= a b for every a,b ∈ Z.====

## PSETS 
_______
**We must keep a couple of fundamental definitions in mind before proceeding**
	**1)** An integer $n$ is even then it can be expressed as $2k$ for some  $k \in \ Z$
	**2)** An integer $n$ is odd then it can be expressed as $2k + 1$ for some  $k \in \ Z$
	**3)** Integers have the same parity if they are both even or both odd
	**4)** $a$ divides $b$ if there exists a value , $n$ , such that $an = b$
	**5)** $gcd(a,b)$ is the largest number which divides both $a$ and $b$ . 
	**6)**  $lcm(a,b)$ is the smallest number which is a multiple of both $a$ and $b$. 
	**7)**  Sums , differences , and products of integers are integers . 
	**8)**  The division algorithm $a = b\times q +r$ , $r$ exists if $b$ does not divide $a$ .  
	
**We must keep a couple of fundamental definitions in mind before proceeding**
## Direct Proof Methods
_____
### Proposition : If *P* $\rightarrow$ *Q* 

### Proof:            Suppose *P*
				.
				.
				.
###                        Therefore *Q* 
==Sometimes we must split things into cases ( odd or even for example )

## WLOG : Without Loss of Generality
----
Some proofs involve cases that logically lead to the same conclusion, however different the assignments of variables are . For example , given two integers whos parities differ  , can be shown by letting $a,b \in Z$ where either $a$ or $b$ differ from one another , the way we chose which variable is odd and which is even is arbitrary and wouldn't change the result of the proof , $\therefore$ we just say    ...

==**WOLOG** let $a$ be an odd integer and $b$ be an even integer  . 

___

# | Contrapositive Proof 
____
Another means of proving statements . Similar to how we'd approach direct proofs however in this scenario we would essentially be treating the **if - then** statement as a contrapositive . **$\neg$ then $\rightarrow$ $\neg$ if** . ==We must also keep in mind negation applies similar to how we have it in logic laws . ==

## PSETS 
**Proposition** :Suppose x ∈ Z. If 7x+9 is even, then x is odd.
In this case the contrapositive equivalent to this proposition is as follows
**Proof :** Parities
**| If x is even , then 7x + 9 is odd** .
	
From here the proof becomes a lot more simple . 
```
Suppose x is even , 
then x can be expressed as 2n 
7(2n) + 9 = 2[(7n) + 4 ] + 1 which is in the form of an odd number -> 2k + 1 . 
```

This method of proof is usually far more simple than approaching it like a direct proof . 

**Proof :**  Parities 
____
**Proposition** Suppose x ∈ Z. If $x^2 −6x+5$ is even, then x is odd.
___

```
Suppose x is even 
then x can be expressed as 2c for some arbitrarily chosen c . 
it follows then that (2c)^2 - 6(2c) + 5 
4c^2 - 12c + 5 -> 2(2c^c - 6c + 3) - 1 -> 2k - 1 which is in the form of an odd number. so when x is not odd our original equation is not even . 
```


**Proof :**  Inequalities 
____
**Proposition** Suppose x, y ∈ R. If $y^3 + yx^2 ≤ x^3 + xy^2$$, then $y ≤ x$.
___

as you can imagine this proof would be a nightmare to solve using the direct method of proof writing , where would we even start ? However, applying the method of **Contrapositive proof** is fairly simpler . 

**Contrapositive** Suppose $y > x$ , then $y^3 + yx^2 > x 3 + xy^2$

==**Note** : When negating equality signs it is paramount to keep in mind what the equality sign becomes after the swap occurs . ==

**Note** : When $x_1 > x_2$ it implies $x_1 - x_2 > 0$ 

we then multiple by the positive value $x^2 + y^2$ 
![[Pasted image 20240604144226.png]]

1) **Suppose $x ∈ R$. If $x^2 +5x < 0$ then $x < 0$**
	**Proof** : Proof. (Contrapositive) Suppose it is not the case that x < 0, so x ≥ 0. Then neither x 2 nor 5x is negative, so x 2+5x ≥ 0. Thus it is not true that x 2+5x < 0.
2) **Suppose $a , b ∈ Z$ if both $ab$ and $a+b$ are even , then $a$ and $b$ are even .**
	**Proof**  : if a or b are odd then $ab$ or $a+b$ is odd 
	**WLOG** let a or b differ in parity , 
	$a = 2k+1$
	$b = 2n$
	$ab = 2k+1*2n$
	$ab = 4kn + 2n$
	$ab = 2(2kn + n)$
	$ab = 2r$ , $\therefore$ $ab$ is even 
	$a+b$ = $2k+1 + 2n$ 
	$a + b$ = $2(kn) + 1$
3) **Suppose $n ∈ Z$. If $3 \nmid n^2$ , then $3 \nmid n$.**
	**Contrapositive**	: if $3\mid n$ , then $3\mid n^2$ 
	$3k  = n$
	$3j  = n^2$
	$3j  = (3k)(3k)$
	$3j = 3(3k2)$
	$n^2 = 3f$
	$\therefore 3\mid n^2
4) **Suppose $x, y ∈ Z$. If $x^2 (y+3)$ is even, then $x$ is even or $y$ is odd**
	**Contrapositive**	
	Suppose $x$ is odd AND $y$ is even , then $x^2(y+3)$ is odd . 
	$x = 2k+1$
	$y = 2n$
	$(2k+1)^2(2n+3)$
	$odd\ \times\ \ odd$ = $odd$
5) **Suppose $x ∈ Z$. If $x^3 −1$ is even, then $x$ is odd.**
	**Contrapositive**	
	if x is even then $x^3 - 1$ is odd
	$x=2k+1$
	$(2k)^3 - 1 )$ = Some even number minus one which is just an odd number . 
6) **Suppose If $n$ is odd, then $8 \mid (n^2 −1)$.**
	**Contrapositive** if $8\nmid\ (n^2 - 1)$ then $n$ is even
	$n = 2k$
	given that 8 **does not divide** $(n^2 -1)$ it implies there exists and r value such that $(n^2 - 1)$ = $8 \times \ q\ +r$ with $0 \lt r \lt 8$ . This proof would take far too long because we would have 7 cases . So a direct proof or proof through contradiction would be more ideal . 
	$8p = (n^2-1)$
	$4k^2 + 4k + 1 - 1 )$
	$4k(k + 1)$


## Proving Non-Conditional Statements
___
This form of proof is utilized when looking at **biconditional** statements . That is the truth value of both statements is codependent on the truth value of the other statement , $P \longleftrightarrow Q$ . In this case we must prove two conditional statements , That is when P implies Q and when Q implies P . 
We can use any method we'd like to prove parts of the statements ( Direct , Contradiction , Contrapositive )  . 
___
## PSETS
**Parity** Pattern
1) Suppose the integer $n$ is odd if and only if $n^2$ is odd . 
	In this case we are proving the truth value of both $P\rightarrow Q$
	and $Q \rightarrow P$ . 
	
	$P \rightarrow\ Q$ :  $n$ can be expressed in terms of $2c+1$  so $(2c+1)^2$ is also odd ( Direct ) 

	$Q \rightarrow\ P$ : if $n^2$ is not odd , then $n$ is odd  (Contradiction) 
	$n = 2k + 1$ 
	$n^2 = 2(2k^2 + k) + 1$ , which is odd , $C \wedge \neg C$ which is impossible . 
	
**Modularity** Pattern
2) Suppose $a$ and $b$ are integers. Then $a ≡ b (mod 6)$ if and only if $a ≡ b (mod 2)$ and $a ≡ b (mod 3)$
	Recall $a \equiv b (mod c)$ if $c\mid a-b$
	
	$P \rightarrow\ Q$ : if $a\equiv b(mod6)$ then $a\equiv b(mod2) \ \wedge \ a\equiv b(mod3)$	
	**Direct Proof** : 
	$6\mid (a-b)$
	$6n = (a-b)$
	$2n = (a-b)$
	$3n = (a-b)$	
	$2(3n) = 6n$ 
	$3(2n) = 6n$ 
	
	$Q \rightarrow\ P$ :  if $a\equiv b(mod2) \ \wedge \ a\equiv b(mod3)$ then $a\equiv b(mod6)$
	**Direct Proof** : 	
	$2n = (a-b)$	this implies (a-b) is even
	$3k = (a-b)$	    this implies k is even otherwise 3k would be odd
	$3(2k) = (a-b)$	
	$6k = (a-b)$	     $\therefore$ $6 \mid (a-b)

## Equivalent Statements
___
- A set of statements where all are true or all are false.
- Essentially proving through means of counter example 
___
**Existence Proofs; Existence and Uniqueness Proofs**
- Conditional statements have the $P(x) \rightarrow \ Q(x)$ this is equivalent to saying$$\forall x , \ P(x) \rightarrow \ Q(x)$$
- However the question arises , How would we prove Existential Statements , Well existential statements can be converted into Universal statements through negation .  $$\neg[\forall x , \ P(x) \rightarrow \ Q(x)] \equiv \exists x ,\  P(x)\  \wedge\ \neg Q(x) $$
- Existence Statements follow the form that there exists at least one $x$ in the set $Q(x)$
	- **Proposition** There exists an even prime number.
		- 2 is both even and prime 


## PSETS
___
**Inequality Pattern** 
1) 7. Suppose x, y ∈ R. Then $(x+ y)^2$ = $x^2 + y^2$ if and only if $x = 0$ or $y = 0$.
	$P \rightarrow\ Q$ : If $(x+ y)^2$ = $x^2 + y^2$ if $x = 0$ or $y=0$  
	**Direct Proof** Expand and simplify $\rightarrow$ $xy = 0$
	
	$Q \rightarrow\ P$ :  
	**Direct proof** : with cases . 
	
**Divisibility Pattern**
2) Suppose a ∈ Z. Prove that 14 | a if and only if 7 | a and 2 | a.
	$P \rightarrow\ Q$ :  if $14\mid a$ then $7\mid a$ and $2\mid a$
	**Direct Proof** : 
	$14n = a$
	$2(7n) = a$ Thus 2 divides $a$
	$7(2n) = a$ Thus 7 divides $a$
	
	$Q \rightarrow\ P$ :  if $7\mid a$ and $2\mid a$ then $14\mid a$
	**Direct Proof** : 	
	$2m = a$ , this implies a is even
	$7k = a$ , this implies k must be even otherwise 7k would not be even 
	$7(2k) = a$   
	$14k = a$  , Therefore 14 divides a 	
	==It is very important to leverage even and odd numbers here	===
	
**Parity Pattern** 	
4) Suppose $a ,b ∈ Z$. Prove that $(a−3)b^2$ is even if and only if $a$ is odd or $b$ is even	
	
	$P \rightarrow\ Q$ :   if $(a−3)b^2$ is even if then $a$ is odd or $b$ is even	
	**Contrapositive proof** : if $a$ is even AND $b$ is odd then $(a-3)b^3$ is odd
	$a = 2c$
	$b = 2k + 1$
	$(2c+2k+1)^2$ = $(even + odd)^2$ = $(odd)^2$ = $odd$ 
		
	$Q \rightarrow\ P$ :  if $a$ is odd or $b$ is even then $(a -3)b^2$ is even
	**Direct proof** : 
	Case 1) **a is odd**
	WLOG let b be odd as well
	$a = 2c + 1$
	$b = 2n$  
	
	$(2c + 1 - 3)(2n)^2$
	$(2c - 2 )(2n)^2$
	$(2[c - 1])(2n)^2$
	$(2[c - 1])(4n^2)$
	$2(c-1)(2n^2)$ 
	
		
	Case 2) **b is even**
	WLOG let a be odd  
**Divisibility Pattern**
5) There exists an n ∈ N for which $11 | (2^n −1)$.	
	$11k =2^n - 1$
	$11k + 1 = 2^n$ this implies $k$ is odd 
	1024
**Irrationality Pattern**
6) Prove that $\sqrt{6}$ is irrational.
	**Proof by contradiction**  : Let $\sqrt{6}$ be rational 
	Then it can be expressed as $a/b$ where either a or b is non even 
	$6 = a^2/b^2$
	$6b^2 = a^2$
	$2(3b^2) = a^2$ so a is even
	$2(3b^2) = a^2$ so a is even
	$6b^2 = (2c)^2$
	$6(b^2) = 2(2c^2)$
	for this to be the case b also must be even otherwise the left hand side of the equation would be odd therefore b must also be even 
**GCD Pattern**
7) There exist no integers a and b for which 21a+30b=1.
	**Proof by contradiction** suppose there exists integers a and b such that 21a+30b = 1
	

____

Tags : #math #discrete-math 