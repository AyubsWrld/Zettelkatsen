## Features of Good Relational Design 
___
- Non-Redundant
	- Changes demand multiple insert changes 
	- Redundancy occurs when we have multiple **functional dependencies** within a table 
### **Functional Dependency**
when a tuple of attributes are dependent or derived from another
The describing *tuple* must be *unique* 
- departmentname tells you the budget and building of the department
- Essentially a *key*
- Given an attribute you can derive a unique attribute (onto)
			*let* $R_1 = \{1,2,3\} , R_2 = \{3,4,5\}$
			$R_1 \times \ R_2$ = $\{(1,4),(1,3),(2,4)\}$
			In this case $1$ maps to both $(3,4)$ , therefore it is not onto .
### **Decomposition** 
- Can be utilized to create shorter query fetching times 
- However not all decomposition are good decompositions . Lossless decompositions are when upon decomposing the table the join will always result in the same table as when we started 
$$R=(A,B,C) ,\ R_1 =(A,B)\ ,R_2=(B,C)$$
===- Ask yourself , If I conduct a decomposition , When I join the tables which resulted from the decomposition , Will I return the the table I had prior to decomposing 
	- **No?** $\rightarrow$ Lossy decomposition 
	- **Yes?** $\rightarrow$ Lossless decomposition  ===
We must also keep in mind that we retain ALL *Functional dependencies* after the decomposition occurs 	.
## Atomic Domains and First Normal Form 
___
### First normal Form
- Domain is atomic if there are no multivariable entities 
- Must be explicit , querying based on substrings is *non-atomic* 
## Decomposition Using Functional Dependencies 
___
**Suppose the following** $\dots$ 
- *Class* (course_id , title , dept_name , credits , sec_id , semester , year , building , room_number , capacity , time_slot_id) 	
	- $courseid^+$ : (course_id , title , dept_name , credits )
	- $(building,roomnumber)^+$ : (building , room_number , capacity)
	- ===$(courseid , secid , semester , year)^+$ : (course_id , sec_id , semester , year , building , room_number , time_slot_id   , dept _name , credits , title )=== This is the primary Superkey . 
## Functional Dependency Theory 
___
- If I have a an attribute within a relation , $R$ , can I derive one or more other attributes given the first . Must be unique .
- $K$ is a *Superkey* for a relation schema $R$ if I can uniquely identify $R$ with $K$ , so $K \rightarrow R$
- A *Candidate Key* implies that there exists no $\alpha \subseteq K$  where $\alpha \rightarrow R$ , That is there is no smaller key which defines $R$ 
	- *ID $\rightarrow$ $R$*
	- *(ID , Name)  $\rightarrow$ R* , Cannot be a Candidate key because ID already uniquely identifies $R$
- **Trivial Functional Dependencies** : When a field determines itself.
- **Closure of Functional Dependencies** : Given a set of Functional dependencies *F* , there exists a transitive relationship between $a , b , c \in F : a \rightarrow b \  ,\  b \rightarrow c$  , so by *Transitivity* , $a \rightarrow c$ . 
- **Steps to Normalizing** 
	1) Generate all functional dependencies
	2) If $F^{+}$ Exists , Decompose . 
- **Armstrong's Axioms** 
	- *Reflexivity*  : (*ID , name $\rightarrow$ name*)
	- *Augmentation*    : (*ID , name $\rightarrow$ name , age*)
	- Transitivity   
![[Pasted image 20240610175142.png]]
- *Members of $F^+$*
	-  $A \rightarrow B$
	-  $A \rightarrow C$	  
	-  $B \rightarrow H$ 
	- By *Transitivity* ,  $A \rightarrow H$	  
	- By *Augmentation* , $AG \rightarrow CG$	  	
	- By *Transitivity* ,  $CG \rightarrow I$	  	
	- By *Transitivity* ,  $CG \rightarrow A$	  	
	- By *Psuedotransitivity* ,  $AG \rightarrow CG \rightarrow H \ , \ \therefore AG \rightarrow H$	  	
	- So the *Superkey* is $AG$	  	
- *Dependency Preservation* : 
## Boyce-Codd Normal Form
---
- Only a singular *Functional Dependency* which does not determine the remaining values within the table ( *Not a Superkey* ) .
- If more than one *Functional Dependency* Exists , Decompose the table and retain one Functional dependency within the Superkey  . 
- Don't normalize multivariable tables .
## Algorithms for Functional Dependencies 
___
## Normalization 
----
- Let $R$ be a relation with some functional dependencies $F$ . 
- Decide whether the Relation is in *BCNF* 
	- Does it have multiple functional dependencies which are not the the Superkey ?
- In the case it is not $\rightarrow$ decompose into a set of relation scheme . 
## Decomposition Using Multivalued Dependencies 
___
## More Normal Form 
___
- 3NF
- 4NF
## Database-Design Process 
___
*26:14*
## Modeling Temporal Data


#programming 