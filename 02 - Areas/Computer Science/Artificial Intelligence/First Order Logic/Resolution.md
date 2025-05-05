Theorem used in proving that proceeds building refutation proofs like **Proof by Contradiction**. Resolution is a single inference rule which can efficiently operate on Conjunctive normal form or clausal form. 
#### Steps
___
- Convert facts into First-Order Logic
- Convert FOL to CNF 
- Negate the statement which needs to be proven ( proof by contradiction ) 
- Draw resolution graph 

#### Example
___
$s_1$ = John likes all kinds of food -> $\forall \ x \ Food(x) \rightarrow Likes(x,John)$
$s_2$ = Apple and Vegetables are food -> $Food(Apple) \wedge Food(Vegetable)$
$s_3$ = Anything anyone eats and is not killed is food -> $\forall \ y ,\  z \ Eats(y,z) \wedge \neg Killed(y) \rightarrow Food(z)$ 
$s_4$ = Anil eats peanuts and is not killed -> $Eats(Anil,Peanuts) \wedge \neg Killed(Anil)$
$s_5$ = Harry eats eats everything Anil Eats -> $\forall \ w \ Eats(Anil,w) -> Eats(Harry,w)$ 
$s_6$ = 
___
Tags : #ai #programming 