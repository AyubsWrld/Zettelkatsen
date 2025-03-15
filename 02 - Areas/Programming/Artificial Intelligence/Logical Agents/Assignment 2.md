### Question 1
___
___
Translate the following Boolean expression in Conjunctive Normal Form: $(A \leftrightarrow B) \leftrightarrow C$. Show your work.

 Convert to Disjunctive Normal Form ( Sum of products ) then converting to Conjunctive Normal Form. 

$$
\begin{array}{|c|c|c|c|}
\hline
A & B & C & ((A \leftrightarrow B) \leftrightarrow C) \\
\hline
F & F & F & F \\
\hline
F & F & T & T \\
\hline
F & T & F & T \\
\hline
F & T & T & F \\
\hline
T & F & F & T \\
\hline
T & F & T & F \\
\hline
T & T & F & F \\
\hline
T & T & T & T \\
\hline
\end{array}
$$

*Disjunctive Normal Form of Min terms ( 0 ):* 
 $$(\bar{A}\bar{B}\bar{C}) + (\bar{A}BC) + (A\bar{B}C) + (ABC)$$
*Utilize DeMorgans law to convert to Product of Sums:* 
 $$(A + B + C)(A + \bar{B} + \bar{C})  (\bar{A}+ B+ \bar{C})  (\bar{A} + \bar{B} + \bar{C})$$
*Logical Representation :* 
 $$(A \vee B \vee  C) \wedge (A \vee \neg{B} \vee \neg{C}) \wedge (\neg{A} \vee B\vee \neg{C})  (\neg{A} \vee \neg{B} \vee \neg{C})$$
### Question 2
___
___

Use the DPLL Algorithm to prove that $D \rightarrow E$  cannot be entailed from the following knowledge base: $$( D \vee E \vee F ) \wedge ( \neg E \vee \neg D \vee F) \wedge (\neg F \vee \neg D \vee E) \wedge ( \neg F \vee \neg E \vee D) $$

Here we wish to show that $KB\not\models (D \rightarrow E)$. If we can prove that inverse, that $KB \models \neg(D\rightarrow E)$, through the use of [[Unit Propagation]] and [[Pure Literal Elimination]] it follows that based on our knowledge base, $D\rightarrow E$ indeed cannot be entailed. 

<center> <h3>Step 1 <br/> Derive pure literals through the negation</h3></center> 
$$\neg(D\rightarrow E)$$
$$\leftrightarrow $$
$$\neg(\neg D \vee E) \ , \ \text{Modus Ponens}$$
$$\leftrightarrow $$
$$D \wedge \neg E \ , \ \text{DeMorgan's}$$
$$\leftrightarrow $$
$$D \ , \ \neg E$$

<center> <h3>Step 2 <br/> Utilize pure literals to satisfy clausal statements </h3></center> 
$$C_1 : (D \ \vee \ E \ \vee \ F) \ , \text{satisfied by } D$$
$$C_2 : (\neg E \ \vee \neg D \ \vee F) \ , \text{satisfied by } \neg E$$
$$C_3 : (\neg F \ \vee \neg D \ \vee E) \ , \text{unsatisfied} $$
$$C_4 : (\neg F \ \vee \neg E \ \vee D) \ , \text{satisfied by both } \ D \ \text{and} \ \neg E$$

<center> <h3>Step 3 <br/> Reduce unsatisfied clauses if possible </h3></center> 
$$C_3 : (\neg F \ \vee false \ \vee \ false) \ , \text{unsatisfied} $$
$$\leftrightarrow $$
$$\neg F$$


<center> Since all three Boolean variables are satisfiable within the context of negating E following from F we can conclude that indeed</center>
$$KB \not\models D\rightarrow E$$
### Question 3
___
___
 Apply the full first-order logic resolution refutation algorithm to infer the conclusion $Shape(y) ∧ Colored(Red, y)$ from the following KB. For each resolution step, specify the substitution used, if any. 
$$1.  \ ¬Cube(x) ∨ Shape(x)$$
	$$2. \ Cube(C)$$
$$3. \ Colored(Red,C)$$
Step 1) Suppose the inverse of the conclusion. ( This becomes our fourth expression )
$$4. \ \neg(Shape(y) \wedge Coloured(Red , y))$$
$$\neg Shape(y) \vee \neg Coloured(Red , y) \ , \ \text{DeMorgan's}$$
Step 2) Perform Resolution & simplify 
$$5.\  ¬Cube(x) ∨ \neg Colour(Red,y) \ \text{Resolving 1 , 4 }$$
$$6.\  ¬Cube(x) ∨ \neg Colour(Red,y) \ \text{Resolving 1 , 4 }$$
$$7.\ Cube(x) \wedge ¬Cube(x) ∨ \neg Colour(Red,y) \ \text{ 2, 6}$$
$$8.\ false ∨ \neg Colour(Red,y) \ \text{ Negation law }$$
$$9.\ \neg Colour(Red,y) \ \text{ Identity law }$$
$$10.\ \neg Colour(Red,y) \wedge Colour(Red,y) \ \text{ 9 , 3}$$
$$11. \ \mathbb{F} $$
Since through negating the conclusion we are left with a contradiction and thus the empty set, it follows that the conclusion holds.

