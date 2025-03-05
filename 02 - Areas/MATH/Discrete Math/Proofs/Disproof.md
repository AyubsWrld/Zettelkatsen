___
**Mathematical Statements** can be categorized as either being *Known to be true* , *Truth Unknown* , or *Known to be False* . 

Usually we begin with a *Conjecture* , that is a statement whose truth value is unknown to us until we conduct some form of test , then we can lump it into one of the known categories . 

**Disproving Universal Statements: Counterexamples**
____
Proving a statement's falsehood can be as simple as showing that for any Proposition $P(x)$ , There exists some value which does not follow the rule which $P(x)$ follows . 

*Take for example $\dots$*

- $P(x)$ states that every prime number is odd . 
- The counterexample would be to show that 2 is both prime and an even number . 
- By doing this we are showing that $\exists \  x \in S : \neg P(x)$ , in this case $x$ is 2  . 

This also applies to when we want to prove conditional statements in the form $\dots$ $$ \forall x \in S : P(x) \rightarrow Q(x)$$ To disprove this statement we simply show that $\dots$
$$\exists \ x \in S : P(x) \rightarrow \neg Q(x)$$
*Suppose the Conjecture* $\dots$
	For every $n \in Z$, the integer $f(n) = n^2 − n+11$ is prime.
	*Disproof.* The statement “For every n ∈ Z, the integer f (n) = n 2 − n + 11 is prime,” is false. For a counterexample, note that for n = 11, the integer f (11) = 121 = 11·11 is not prime. A
	
===In disproving a statement with a counterexample, it is important to explain exactly how the counterexample makes the statement false. Our work would not have been complete if we had just said “for a counterexample, consider n = 11,” and left it at that. We need to show that the answer f (11) is not prime. Showing the factorization f (11) = 11·11 suffices for this.=== 

*Suppose the Conjecture (Set Example)* $\dots$
	To see where this counterexample came from, draw Venn diagrams for A −(B∩C) and (A −B)∩(A −C). You will see that the diagrams are different. The numbers 1, 2 and 3 can then be inserted into the regions of the diagrams in such a way as to create the above counterexample.
	
**Disproving Existence Statements** $\dots$
	This is simply showing that for $\forall x \in S : P(x)$

*Suppose the Conjecture* $\dots$
	There is a real number $x$ for which $x^4 < x < x^2$ .

**Disproof by Contradiction** $\dots$
- Simply assume P to be true and arrive at a contradiction .

## PSETS $\dots$ 

- if $x ,y \in \mathbb{R}$ , then $|x + y| = |x| + |y|$
	- The conjecture, if $x ,y \in \mathbb{R}$ , then $|x + y| = |x| + |y|$ , is false . For counterexample , *let*       $x = 2 , y = -3$ , $|2 + (-3)|$  $\neq (|2| + |3|$ 
- For every $n \in \mathbb{N}$ , the integer $2n^2 - 4n + 31$ is prime . 
	- For every $n \in \mathbb{N}$ , the integer $2n^2 - 4n + 31$ is prime . 
	- The conjecture ,   For every $n \in \mathbb{N}$ , the integer $2n^2 - 4n + 31$ is prime  , is false . for counterexample , *let* $n = 31$ 
- For every $n \in \mathbb{Z}$ , $n^5 -n$ is even , then $n$ is even . 
	- Suppose for sake of contradiction ,  $n^5 -n$ is even 
	- Since the difference of two values results in an even value their parities of the operands must be the same 
	- Case N is even $\rightarrow$ $(2n)^5 = 32n^5 = 2(16n^5)$ which is even  , subtracting an even number would also yield an even number 
	- This conjecture is true . 
- For every $n \in \mathbb{N}$ , the integer $n^2 - 17n + 17$ is prime . 
	- This conjecture is false , for counterexample suppose $n = 17$
- If $a,b \in \mathbb{N}$ , then $a+b < ab$
	- For sake of contradiction suppose that If $a,b \in \mathbb{N}$ , then $a+b < ab$ is true , *let* $a = 1 , \ b = 2$ .
	- $1 +2 = 3$
	- $1\times2 = 2$
	- $3 < 2$ is false , and therefore the conjecture is also false .  

[[Proof Writing]] [[Proofs Involving Sets]]