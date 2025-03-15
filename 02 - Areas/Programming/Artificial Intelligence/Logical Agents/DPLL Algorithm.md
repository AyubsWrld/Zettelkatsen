A backtracking algorithm that improves the brute force approach to solving the Boolean Satisfiability Problem ( SAT ) Through the use of [[Unit Propagation]] and [[Pure Literal Elimination]].

> [!example] 
> Use the DPLL Algorithm to prove that $D \rightarrow E$  cannot be entailed from the following knowledge base: $$( D \vee E \vee F ) \wedge ( \neg E \vee \neg D \vee F) \wedge (\neg F \vee \neg D \vee E) \wedge ( \neg F \vee \neg E \vee D) $$
> 

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
___
Tags : #programming #artificial-intelligence