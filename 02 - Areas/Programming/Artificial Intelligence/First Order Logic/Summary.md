# <mark style="background: #FFB86CA6;">8 first-order logic.</mark> 
___
Propositional logic works if we are simply representing basic concepts of logic. However if we want to be more expressive we must use <mark style="background: #ABF7F7A6;">first order logic.</mark>  
### 8.1 Representation Revisited 
___
Programming languages are really good at representing independent facts. In Wumpus World for example, utilizing an array to signify some boolean is not hard ( *[2 , 2] <- wind*  to signify the presence of wind ). Programming languages usually lack the capability to represent knowledge that may be inferred. 


### 8.2 Syntax and Semantics of First-Order Logic
___
#### 8.2.1 Models for first-order logic 
- The **Domain** of a model is the set of objects it contains. The objects within the model may be related , said relations are represented through the use of tuples. For example {( Richard the Lionheart , King John ) , (King John , Richard the Lionheart)} could be an example of one such relation within a model.
#### 8.2.2 Symbols and interpretations 
___
- Come in three kinds 
	- Constant symbols 
	- Predicate symbols 
	- Function symbols 
- Each model must provide the information required to determine if any given sentence is true or false. 
- A model in first-order logic consists of a set of objects and an interpretation that maps the set of objects via relations between them. 

#### 8.2.3 Terms
___
- Logical expression that refers to an object , for example , LeftLeg(John) Refers to King Johns left leg. This is an example of a complex term. A function symbol follow by arguments of values with which go into the function and resolve to an object. 
- These are not to be mistaken by subroutines however. 
- function symbol $f$ applied to some objects within the domain of the model $\{ d_1 , d_2 , \dots , d_n\}$ and resolve to some value. 

#### 8.2.4 Atomic Sentences 
___
-  Atomic sentences are formed from a predicate symbol and optionally followed by a list of arguments which are objects within the domain of the model. 
	- For example: $Brother(Richard,John)$
- These atomic sentences resolve to either true or false. 
#### 8.2.5 Complex Sentences 
___
-  We can utilize atomic sentences in tandem with logical connectives to produce more complex sentences. 
	-  $\neg Brother(LeftLeg(Richard),John)$

#### 8.2.6 Quantifiers 
___
- Used to express properties of entire objects. For example 
	- $\forall x \ King(x) \rightarrow Person(x)$ ( Universal Quantification )
- A **Variable** is an unknown usually expressed as a lowercase letter ( $x$ in the example above ).
- A term with no variables is called a ground term. 

#### 8.2.7 Equality
___
- Predicate logic includes one more way to make atomic sentences, rather than using other predicate symbols we can reap the same effect through the use of the equivalence operator ( = ). 
	-  $Father(John) = Harry$
- It can also be used to state facts 
	- $Brother(x , y) \rightarrow \neg(x=y)$
- To say that Richard has at least two brother  
- $\exists x , y Brother(x,Richard) \wedge Brother(y,Richard) \wedge \neg(x = y))$  
- **Unique-names assumption** 
- **Closed-world Assumption** 

### 8.3 Using First-Order Logic 
____

#### 8.3.1 Assertions and queries in first-order logic 
___
- Sentences are added to a knowledge base through the use of TELL ( assertion ). 
- We can assert that John is a King , Richard is a Person , and all Kings are people 
	- TELL(KB, King(John))
	- TELL(KB, Person(Richard))
	- TELL(KB, $\forall x King(x) \rightarrow Person(x)$)
- We can also Ask questions and receive boolean responses utilizing ASK(KB , King(John)). 
	- Resolves to true.
- We can also use ASKVARS to get a more descriptive return value than 
#### 8.3.2 The kinship domain 
___
- Relations between families such as "Elizabeth is the mother of Charles" and "Charles is the Father of William". 
#### 8.3.4  Wumpus World 
___
- Recall that Wumpus receives a  percept vector with five elements. The corresponding first-order sentence stored in the knowledge based must include both the percept and the time which it occurred otherwise the agent will get confused about when it saw what.  
	- Percept([Stench , Breeze , Glitter, None , None], 5)
- The actions in Wumpus World can be represented by the following [[Logical Terms]]. Turn(Right) , Turn(Left) , Forward , Shoot , Grab , Climb 
- We can determine the best action through querying the knowledge base using the AskVars(KB,BestAction(a,5)). Which returns a binding list of substituted variables with their values $\{a/Grab\}$ 
- The raw percept data implies certain facts about the current state. For example: 
	-  $\forall \ t \ , s \ , g \  , w \ , \ c \ Percept([s , Breeze , g , w , c ],t) \rightarrow Breeze(t)$
	-  $\forall \ t \ , s \ , g \  , w \ , \ c \ Percept([s , None , g , w , c ],t) \rightarrow \neg Breeze(t)$
	-  $\forall \ t \ , s \ , g \  , w \ , \ c \ Percept([s , b , Glitter , w , c ],t) \rightarrow Glitter(t)$
	-  $\forall \ t \ , s \ , g \  , w \ , \ c \ Percept([s , b , None , w , c ],t) \rightarrow \neg Glitter(t)$
- Simple reflex behaviour can also be implemented by quantified implication sentences. For example:
	- $\forall \ t \ Glitter(t) \rightarrow BestAction(Grab,t)$

# <mark style="background: #FF5582A6;">9 INFERENCE IN FIRST-ORDER LOGIC
</mark>

___

## 9.1 Propositional vs. First-Order Inference
___
- One way to do first-order inference is to convert the first order knowledge base to propositional logic and use propositional inference. This can be done in a step by step manner.
	1. **Remove Quantifiers** through the use of either [[Universal Instantiation]] or [[Existential Instantiation]]. 
		1. **Example** : From the sentence $\exists \ x \ Crown(x) \wedge OnHead(x,John)$ we can infer the sentence $Crown(C_1) \wedge OnHead(C_1 , John)$. *<mark style="background: #D2B3FFA6;">Note: When using existential quantifiers we can only utilize the variable once.</mark>
		2. In short we are only supplying a name to a variable within the knowledge base which we know to have some attribute. 

### 9.1.1 Reduction to Propositional Inference.
____
- In the case we decided to go with [[Universal Instantiation]] we must instantiate every [[Object within]] the knowledge base. For example suppose our [[Knowledge Base]] contained the sentences.
	- $\forall \ x \ King(x) \wedge Greedy(x) \rightarrow Evil(x)$
	- $King(John)$
	- $Greedy(John)$
	- $Brother(Richard)$
- Since the only Objects are John and Richard we substitute both for our variables x => $\{ x/John , x/Richard\}$ from doing this we obtain. $King(John) \wedge Greedy(John) \rightarrow Evil(John) , King(Richard) \wedge Greedy(Richard) \rightarrow Evil(Richard)$ 
- Next we replace ground [[Atomic Sentences]] like $King(John)$ with proposition symbols like $JohnIsKing$. 
- This inference process can be captured as a single inference rule that we call Generalized Modus Ponens

## 9.2 Unification and First-Order Inference
____
When we convert our First-Order Knowledge base into a propositional knowledge base we run the risk of generating multiple unnecessary terms. It would be far easier to just propositionalize only the portions of the [[Knowledge Base]]  which aid in inference. For example, Given the rule that greedy kings are evil, Find some x such that x is a king and x is greedy and then infer that x is also evil . 

### 9.2.1 Unification 
___
The unify Algorithm takes two sentences and returns a unifier for them ( a substitution ) if one exists. 
$$Unify(Knows(John,x),Knows(John,Jane)) = \{x/Jane\}$$
$$Unify(Knows(John,x),Knows(y,Bill)) = \{x/Bill , y/John\}$$
It is essentially like Finding substitutions for variables such that the statement is coherent. 

## 9.3 Forward Chaining 
____

### 9.3.1 First-order definite clauses
____
First-order definite clauses are disjunctions of literals of which exactly one is positive. If you see x in a definite clause it implies that there is a $\forall x$ quantifier. A typical First-order definite clause looks like this : $$King(x) \wedge Greedy(x) \rightarrow Evil(x)$$
The literals King(x) and Greedy(y) also count as definite clauses. 

### 9.3.2 A simple forward-chaining algorithm 
___
Used to determine whether [[Atomic Sentences]] are entailed by a knowledge base given a set of [[First-Order Definite Clause]]s.  

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