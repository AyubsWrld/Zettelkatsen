![[Pasted image 20241007090357.png]]
#### DFS ( Lexicographic order )
____
1) Fish 
2) Fish Human
3) Fish Human Tiger , No more things to add to the stack so popping ensues 
4) tiger , human fish (Result of popping from the stack)
5) plankton 
6) Plankton , Shrimp , No more things to add to the stack so popping ensues 
7) Shrimp , Plankton (Result of popping from the stack)
8) sheep , No more things to add to the stack so popping ensues 
9) sheep  (result of popping from the stack)
10) wheat , no more things to add to the stack so popping ensues 
11) wheat ( Result of popping from the stack)
12) tiger , human , fish , shimp , plankton , sheep , wheat 

#### Removing Sources 
____
We remove sources ( No incoming values ) based on the greater lexicographic order . Plankton > wheat so we remove wheat . wheat and shrimp become sources , so we remove shrimp . shrimp and fish become sorces so we remove wheat . fish and sheep are sources so we remove sheep . human and fish are sources 
 ___
 Tags : #programming #algorithms 