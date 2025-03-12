___
Tags : #ai
____

What is Wumpus World ? ;; Common AI test environment used to explore how logical agents operate in uncertain conditions . 


What are the characteristics of Wumpus World ? ;; Wumpus world is a grid-based world wherein the agent has limited sensors , Actions include **moving, turning, grabbing, releasing, and shooting**. World is **partially observable**, **deterministic**, **static**, and **single-agent**. Success depends on **logical reasoning, safe exploration, and strategic risk-taking**.


What is a knowledge base ? ;; A set of knowns about the environment. Could be perceived truths or rules . 

What is the structure of a Knowledge-base ? ;; Propositional logic ( If x -> y ) . The agent can add new facts and derive conclusions from existing ones . 

What is a Declarative Approach to building agents ? ;; Answer 

Why would we want to take a Declarative Approach to building agents ? ;; Answer 

What are the two Design levels of declarative approach ? ;; Knowledge & Implementation 

What is entailment ? ;;**Entailment** is the logical relationship where a set of sentences (**KB**) necessarily implies another sentence (**α**), meaning **α must be true in all models where KB is true** (denoted as **KB ⊨ α**).

What is an example of entailment ? ;; $B$ : Socrates is mortal , $A$ : Socrates is a man . 

What is a model? ;; A function which assigns a truth value to a set of propositional statements creating a configuration . 


What is an Inference ? ;; A process of deriving new truths from known ones. 

What is an example of an inference ? ;; Every time I shower my hair gets wet , I showered so that means my hair it wet . 

What is *Modus Ponens*? $P \rightarrow Q , P  \ \therefore Q$

What makes an inference sound ? ;; An inference is sound *iff* it generates only entailed sentences. 

What is an entailed sentence ? ;; A propositional statement which is true given our knowledge base is true 

What is a complete inference system? ;; An inference system is complete if it can derive every sentence that is entailed by the knowledge base.

What is Satisfiability ? ;; A sentence ( Propositional statement ) is satisfiable if it is true in some model. That is if we introduce it into a model an impossibility wont arise . 

What is full resolution rule ? ;; Rule in which two complimentary literals can be removed from a statement 

What does $(P\vee Q)$ , $(\neg P \vee R)$ resolve to using full resolution ? ;; $( Q \vee R)$ . 

What is clause form ? ;; Conjunctive Normal Form ( Product of sums ).

What is Disjunctive Normal Form ? ;; Sum of Products.

Convert the following sentence to clause form : $(A \vee \neg B) \rightarrow ( C \wedge D )$ ;; Result : $\{ \neg A \vee C , \ \neg A \vee D \ , B \vee C , \ B\vee D\}$

Convert the following sentence into clause form : $B_{1,1} \leftrightarrow ( P_1 , P_2 )$ ;; try it 









