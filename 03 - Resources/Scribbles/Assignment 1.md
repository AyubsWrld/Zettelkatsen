#### CMPT355
#### Assignment 1 | Simple Reflex Agent
#### Ayub Mohamed 

### Exercise 1

**a) Design a rational simple reflex based vacuum agent for the following situation**

```c
function SIMPLE_REFLEX_VACUUM_AGENT(percept) 
/* INPUT: percept contains:
   - current_room: which room agent is in (0-5)
   - rooms[]: array of room states ( I assumed they were class objects ) (DIRTY/CLEAN) for all 6 rooms
   OUTPUT: action to take (SD, CW, CCW, or SI)
*/
	if percept[current_room].isDirty then
		SD 
		return CW// Direction is arbitrary 
	// Otherwise just move clockwise 
	return CW		
```

**Why the problem is trivial and further explanation** : Since the performance measure is based solely on the number of clean rooms at the end of 11 actions , we can begin at any arbitrary room and exhaustively go through every room and clean them . Since the worst case cost *( every room including the starting room being dirty )*  is 11 actions then this simple snippet of code will be considered rational when examined utilizing the performance measure  . 

**b) The reason why this agent is rational because:**
- It cleans dirty rooms immediately when encountered
- Since the performance measure is solely contingent on the number of rooms  after 11 actions  , we only concern ourselves with moving and cleaning at any chance we get as in the worst case scenario ( 11 actions ) all rooms will be clean regardless of whether we chose to rotate clockwise or counter clockwise . 
- It continues moving when no immediate dirty rooms are found, ensuring complete coverage

**c) How would the answer change (design and explanation) if the performance measure was applied from the initial moment?**  When the performance measure is applied at the initial moment the direction no longer is arbitrary.  We must now tailor the design of our agent so that we  maximize the sum of the current performance measures over the course of 11 actions . We can represent this relation between steps taken and the performance measure as a summation . 

$$\sum_{t=0}^{11} F(t)$$

where $F(t)$ represents the number of clean rooms at time step $t$. For a 6-room environment, $0 \leq F(t) \leq 6$ at any time $t$. Our new algorithm is can be implemented as follows ...

```c
function SIMPLE_REFLEX_AGENT(percept)
/* INPUT: percept contains:
   - current_room: which room agent is in (0-5)
   - rooms[]: array of room states ( I assumemd they were class objects ) (DIRTY/CLEAN) for all 6 rooms
   OUTPUT: action to take (SD, CW, CCW, or SI)
*/
    // If current room is dirty, clean it
    if rooms[current_room].isDirty then 
        return SD
    // Check clockwise room for dirt
    clockwise_room = (current_room + 1) % 6
    if rooms[clockwise_room].isDirty then 
        return CW
    // Check counterclockwise room for dirt
    
    counterclockwise_room = (current_room - 1 + 6) % 6
    if rooms[counterclockwise_room].DIRTY then 
        return CCW
        
    // Find any dirty room and choose shortest direction
    for offset = 2 to 3:
        // Check clockwise
        clockwise_check = (current_room + offset) % 6
        if rooms[clockwise_check].DIRTY then  
            return CW
            
        // Check counterclockwise
        counterclockwise_check = (current_room - offset + 6) % 6
        if rooms[counterclockwise_check].isDirty then  
            return CCW
    // If no dirty rooms found
    return SI    
```

**d) With the possibility of incurring penalties :**

```c
function PENALTY_AWARE_REFLEX_AGENT(percept) 
/* INPUT: percept contains:
   - current_room: which room agent is in (0-5)
   - rooms[]: array of room states ( I assumemd they were class objects ) (DIRTY/CLEAN) for all 6 rooms
   OUTPUT: action to take (SD, CW, CCW, or SI)
*/
	// Helper function to derive the dirty rooms using the percept 
	
    dirty_neighbors = CountDirtyNeighbors(percept)
    
    if percept[current_room_number].isDirty then  
        // Clean only if adjacent rooms are also dirty ( worth the 2-point penalty )
        if dirty_neighbors ≥ 1 then  
            return SD  // Penalty of 2 but creates clean cluster
	   else 
            return SI  // Not worth 2-point penalty for isolated dirty room
    
    // If the current room clean, move only if multiple dirty rooms are adjacent
    if dirty_neighbors ≥ 2 then  
        // Worth 1-point movement penalty to reach cluster of dirty rooms
        return PolarToMostDirtyRooms(percept)
    
    return SI  // Default to idle so we may avoid incurring any penalties
```

Motivation:
Here our agent only cleans when it is most beneficial to do so ( when there are adjacent dirty rooms to minimize movement penalties ) . The agent is designed with a preference to staying idle over isolated cleaning actions due to the high cost trade off SD poses (2 points) . Our agent also moves only when multiple dirty rooms are within reach to compensate for movement penalties . This takes advantage of the nature of the problem as the state of the rooms are fully observable . 

**e) partially observable environment:**

```c
function PARTIAL_OBSERVABLE_REFLEX_AGENT(percept) 
/* INPUT : ( percepts ) the current room the agent is in and the status of the    * rooms . 
 * STATE : Current State of the room the agent is currently in ( dirty / clean ) 
 * Potential Actions : Suck dirt , Stay idle , Move (CW , CCW ). 
*/   
    if percept[current_room_status].isDirty then 
        return SD
    
    // Simple clockwise exploration since we can't see other rooms
    return CW  // Always move clockwise when in clean room
```

 This constraint causes the problem to degenerate to the first problem . Since we cannot optimize movement direction since neighboring rooms are not visible . The agent uses consistent clockwise movements to ensure eventual complete coverage of all the rooms . The reason why this strategy is rational because the agent immediately cleans dirty rooms when found , systematically moves to the next room to pattern prevent getting stuck and will eventually visit all rooms in the circular environment. Since we are constrained by agent's limited knowledge we cannot make a more informed decision of how to proceed . On the bright side the reduction in sensor capability simplifies our agent's decision-making process .

# Exercise 2 

### **a) Rational Agent Design** 

Since the agent is has no percepts and we wish to design a simple reflex agent , the best course of action would be randomizing its actions and letting the performance measure eventually represent some form of *Normal Distribution* . 
#### Pseudocode 

```c
function RATIONAL_VACUUM_AGENT( void )
    // First decide whether to clean or move
    cleaning_decision = RANDOM(1, 2)  // Generates either 1 or 2
    
    if cleaning_decision = 1 then  
        return SD  // Suck Dirt
        
    //We then choose where to move , since our movements are not penalized , it is never useful to stay idle ( SI ) 
    
	movement_decision = RANDOM(1, 4)
	if movement_decision = 1 then 
		return "right"
	else if movement_decision = 2 then 
		return "left"
	else if movement_decision = 3 then 
		return "up"
	else movement_decision = 4 then 
		return "down "
// Helper function  | generates random number between min and max ( this calculates inclusively )
function RANDOM(min, max)
    return floor(RANDOM() * (max - min + 1)) + min
```

### **b) Explain why the agent is rational ?** 
Since our agent lacks any form percept and memory our best bet to maximize the agents performance would be to randomly go through our possible actions and hope for the performance measure to resemble a normal distribution if the number of times the agent has acted is large enough . 


### **c) Then make it a rational model-based agent?** 
Since our agent has **no idea where it is** due to the lack of any percept , it must operate under the assumption that **any action could be happening anywhere**. the best strategy is the one purposed in *part b* of this exercise if we assume that our agent is truly sensor less 

### **d) Then make it a rational model-based agent?** 
As previously mentioned our agent has **no idea where it is**, it must operate under the assumption that **any action could be happening anywhere**. 