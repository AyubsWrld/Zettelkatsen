## Equivalent Equations . 
---
$$ A \times B \equiv \{(x,y) : x\in A\ , y\in B\}$$
$$A \ \cup \ B \equiv \{ x:(x\in A) \  \vee \ (x\in B)\}$$
$$A \ \cap \ B \equiv \{ x:(x\in A) \  \wedge \ (x\in B)\}$$
$$A \ - \ B \equiv \{ x:(x\in A) \  \wedge \ (x\notin B)\}$$
## **How to Prove $a\in A$**
- Recall *set builder notation* where we had some value , $x$ , be expressed in terms of following some rule , $P(x)$  in the form $A = \{x : P(x)\}$
	-  $\{x : \ x \ is \ a \ odd \ number \}$ = $\{\dots ,-5 , -3 , -1 , 0 , 1 , 3 , 5 , \dots \}$ 
	- To prove this we simply must prove that $P(a)$ is true 
- Similarly , when we have the prior half of the expression expressed in terms where the variable is said to belong to another set we must also prove that said variable also belongs within the first set  . 
	- $\{x \in S : P(x)\}$
		-  in this case $x$  must exist in $S$  *AND* $P(x)$ must be true 	
## How to Prove $A \subseteq B$ 
- Simply we show that for every $x \in A$  , $x \in B$ . But for it to be A *PROPER* subset , there must  exists $\exists y : (y \in B) \wedge \ (y \notin A)$
**Suppose the following $\dots$**
$A \times (B \cap C) \dots$ 
- $\{(x , y)  : (x \in A)  \ \wedge \ (y \in B \cap C) \}$ , *Definition of Cartesian Product*
- $\{(x , y) : (x \in A)  \ \wedge (\ y \in B \wedge y \in C) \}$ , *Definition of Intersection*
- $\{(x , y) : (x \in A)  \ \wedge (x \in A) \wedge (\ y \in B \wedge y \in C) \}$ , *$P = P \wedge P$*
- $\{(x , y) : (x \in A)  \ \wedge (x \in A) \wedge (\ y \in B \wedge y \in C) \}$ , *$P = P \wedge P$*
- $\{(x , y) : [(x \in A)  \ \wedge (y \in B)] \wedge [(\ x \in A) \wedge ( y \in C)] \}$  
- $(A \times B) \cap (A \times C)$ 
$\overline{A \cap B} \dots$ 
	
	
	
- $\{x : (x \notin A \cap \ x \notin B)\}$ , *Definition of Compliment*
- $\{x : (x \notin A) \wedge \ (x \notin B)\}$ , *Definition of Union*
- $\{x : (x \notin A \wedge \ x \notin B)\}$  
- $\{x : x \notin (A \vee B)\}$   , *Demorgans*
- $\{x : x \notin (A \cup B)\}$   , *Definition of Union*
- $\bar{A} \cup \bar{B}\dots$ 
## *PSETS* 
**Subset Pattern**
- Prove that  given:  $S_1 = \{12n : n\in Z\}$ $\subseteq$  $S_2 = \{3n : n\in Z\}$ $\cap \  S_3 = \{2n : n\in Z\}$
	- This is essentially saying that every value which appears within $S_1$ appears in union of the other sets
	- How can we prove this ? If we can show that or any value which occurs within $S_1$ , a value exists within $S_2$ or $S_3$ such that they divide the arbitrary value found within $S_1$ . 

