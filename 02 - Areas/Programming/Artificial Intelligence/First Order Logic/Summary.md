
### <mark style="background: #FF5582A6;">Problem with propositionalizing knowledge base</mark>
___
The main problem with propositionalization is that is sometimes generates useless statements. 
- Given the rule:  
	$∀x (King(x) ∧ Greedy(x) → Evil(x))$
- And facts:  
	$King(John), ∀y Greedy(y), Brother(Richard, John)$
- The **correct** inference is $Evil(John)$.
- However, propositionalization produces **irrelevant facts** like **Greedy(Richard)**, which are unnecessary for the final conclusion.
	  
- So if we have $p$ predicates ( rules ), each with $k$ argument, and $n$ constants then the number of possible ground statements ( substituting arguments with constants ) = $p \cdot n^k$ .

To **Solve** this we utilize **Lifting** and **Unification**. As opposed to converting the entire knowledge base from **First Order Logic** into **Predicate Logic** we can lift inference rules into **FOL** using techniques like **generalized Modus Ponens** and **Unification**.
  
### <mark style="background: #FF5582A6;">Lifting</mark>
___
 the process of generalizing inference rules so that they apply to logical expressions with variables to avoid unnecessary substitutions. Instead of instantiating $\forall x P(x) \rightarrow Q(x)$ for all possible x, inference applies only where necessary. 

#### <mark style="background: #FF5582A6;">Unification</mark> 
___
 Allows different logical expressions to be matched based on their variable substitutions. Given **P(Alice)** and **P(x) → Q(x)**,**Unification** allows **x = Alice**, leading directly to **Q(Alice)** without instantiating unnecessary terms.
 

___
Tags : #ai #programming 