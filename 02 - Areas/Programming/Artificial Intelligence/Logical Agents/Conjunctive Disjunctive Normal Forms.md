
> [!example] 

### *$\text{Let}$* $S = (A \leftrightarrow B) \leftrightarrow C$ , translate to Conjunctive Normal Form ( Product of Sums )

##### ===**Step 1)**=== : Populate truth table.

> [!tip] 
> $A \leftrightarrow B$   is logically equivalent to $(A \rightarrow B) \wedge (B \rightarrow A )$

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


#### ===**Step 2)**=== : Express the Disjunctive Normal Forms ( Sum of Products ) of the max terms ( 0 ).
### $$(\bar{A}\bar{B}\bar{C}) + (\bar{A}BC) + (A\bar{B}C) + (ABC)$$
#### ===**Step 3)**=== : Apply *DeMorgan's Law* to derive the Conjunctive Normal Form ( Product of Sums ) 
 $$(A + B + C)(A + \bar{B} + \bar{C})  (\bar{A}+ B+ \bar{C})  (\bar{A} + \bar{B} + \bar{C})$$
___
Tags : #programming #artificial-intelligence