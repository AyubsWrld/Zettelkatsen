KB |= $\lambda$ , KB true -> $\lambda$ true. 
- (A∨B)(A \lor B)(A∨B)
    
- (¬B∨C)(\lnot B \lor C)(¬B∨C)
    
- (C∨A)(C \lor A)(C∨A)

A , C one polarity -> pure , B not pure. 

$DPLL(\{ Clauses\} , \{variables\} , \{assignments\})$  , "Infer x -> KB |= x ? -> prove KB |= $\neg x$ doesn't work 


 Perceptron 
 Simple Neural Networks 
 Backpropagation for perceptron 
 Training NN 
 Convolutional NN 
 Recurrent NN


$A \vee B \rightarrow C$
$B \vee C \rightarrow D$
## CNF 

 $(\neg A \vee C ) \wedge (\neg B \vee C)$  
 $(\neg B \vee D ) \wedge (\neg C \vee D)$  

## Negate conclusion $A \rightarrow D$ 
$\neg(A \rightarrow D)$
$\neg(\neg A \vee D)$
$(A \wedge \neg D)$
### These become clauses
C1: $\neg A \vee C$
C2: $\neg B \vee C$  
C3: $\neg B \vee D$
C4: $\neg C \vee D$  
C5: $A$
C6: $\neg D$

Pure literals ? None 
Unit Clauses ? $\neg D , A$  -> set $\neg D$ to true. 

C1: $\neg A \vee C$
C2: $\neg B \vee C$  
C3: $\neg B \vee D$ => $\neg B$
C4: $\neg C \vee D$  => $\neg C$
C5: $A$
C6: $\neg D$ Satisfied 

Not all clauses true
No clauses false 
so we continue 

Pure literals ? None 
Unit Clauses ? $A , \neg B , \neg C$  -> set $A$ to true.

C1: $\neg A \vee C$ => $C$ 
C2: $\neg B \vee C$  
C3: $\neg B$
C4: $\neg C$
C5: $A$ Satisfied 

Clauses 1 and 4 return false leading to an impossibility -> $\neg (A \rightarrow D)$ therefore $(A \rightarrow D)$ is entailed by KB 






