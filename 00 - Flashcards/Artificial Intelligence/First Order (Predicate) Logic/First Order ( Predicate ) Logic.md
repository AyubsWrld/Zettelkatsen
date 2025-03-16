___
Tags : #ai
____

What logical connective does Universal Quantifier use ? ;; An implication connective $\rightarrow$

Assuming At(x , MU ) means x attends Massachusetts University and Smart(x) implies that x is smart , how can we convey that every x at Massachusetts University is Smart ? ;; $\forall x At(x,MU) \rightarrow \text{Smart}(x)$ 

What is an Existential Quantifier ? ;; There exists at least one variable within a set which has an attribute.

What is the logical connective used in an Existential Quantifier ? ;; $\wedge$ 

What does this mean: $\exists x \ \forall \ y \ Loves(x,y)$ given that x loves y? ;; There exists one person who loves everyone.

express as existential Quantification $\forall x \ Likes(x,IceCream)$? ;; $\neg \exists x \neg Like(x,IceCream)$ . *There doesn't exist a single person who doesn't like ice cream*.

What is a Substitution ? ;; The process of substituting variables  ( unknowns ) within a sentence with terms.

*Let Substitution $\theta = \{ x/jane , y/Bob\}$ and Sentence = $S = Knows(x , y)* after applying the substitution what does it resolve to ? ;; $Knows( Jane , Bob )$ , or Jane knows Bob. 

When is Substitution usually used ? Unification. $\theta = \{x/OJ , y/Bob\}$ $Knows(x, Bob)$ , $Knows(OJ , y )$ 

What is a percept sentence ? ;; Captures what the agent is sensing at a given time step. 

Explain this percept sentence : $Percept([Stench,Breeze,Glitter,None,None], 5)$ ;; Agent senses a stench , breeze glitter, and two null percepts at time step 5. 

Given a Percept sentence what does the agent do next ? ;; Queries the knowledge base. $\exists a \ BestAction(a , 5)$ returns false if there isn't. 

Explain this $∀tGlitter(t)∧¬Holding(Gold,t)⇒BestAction(Grab,t)$ ;; For every time step wherein the agent is perceiving gold and they are not holding gold the best action is to grab the gold. 

What is a diagnostic rule ? ;; Diagnostic Rule goes from effect to cause $\forall s \ Breeze(s) \rightarrow \exists r adjacent(r,s) and pit(r)$ 

  