a) Pseudo code 

```
Algorithm SIMPLE-REFLEX-VACUUM-AGENT(percept) 
    // INPUT ( percepts ) the current room the agent is in and the status of the rooms . 
    
    if current_room.isdirty then
	    SD 
	    Move clockwise // Direction is arbitrary 
	else 
	    Move clockwise 
	
	    
```

b) This agent is rational because:
- It prioritizes cleaning dirty rooms immediately when encountered
- Since the performance measure is solely contingent on the number of rooms  after 11 actions  , we only concern ourselves with moving cleaning and moving any chance we get as in the worst case scenario ( 11 actions ) all rooms will be clean regardless of whether we chose to rotate clockwise or counter clockwise . 
- It continues moving when no immediate dirty rooms are found, ensuring complete coverage

{ A :  1 , B  : 0 , C :  1 , D :  1 }
{ A :  starting , B  : { 1  , 4 } , C : { 2 , 3 } , D :  { 3 , 2 } } 
{ A :  starting , B  : { 1  , 4 } , C : { 2 , 3 } , D :  { 3 , 2 } } 

starting idx = A  ; 


idx clean or not ->  0 

if agent doesn't know completely randomize the actions . 