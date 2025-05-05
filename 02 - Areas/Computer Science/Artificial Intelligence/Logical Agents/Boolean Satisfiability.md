Given a Boolean Formula, is there an assignment of truth values ( True / False ) to its variables such that the formula evaluates to true ? 


>[!example]
>
*Let* $S$ = $(A∨¬B∨C)∧(A∨B)∧(¬A∨C)$

This set of Boolean expressions is given to us in [[Conjunctive Normal Form]]. The first clause $A∨¬B∨C$ evaluates to true *iff* either $A$ is true , $\neg B$ is true , or $C$ is true. The second clause, $A∨B$, only evaluates to true *iff* either $A$ or $B$ is true. And the last clause only evaluates to true if $\neg A$ or C is true. With all these in mind a possible configuration would be $A \ , \neg B \ , C$ . And since there is at least one configuration of $A , \ B ,\ C$ wherein $S$ is true, $S$ is considered to be satisfiable. 

___
Tags : #programming #artificial-intelligence