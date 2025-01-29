#### CMPT355
#### Assignment 1 | Simple Reflex Agent
#### Ayub Mohamed 

### Exercise 1

**a) Design a rational simple reflex based vacuum agent for the following situation**

```c
function SIMPLE_REFLEX_VACUUM_AGENT(percept) 
/* INPUT : ( percepts ) the current room the agent is in and the status of the    * rooms . 
 * STATE : Current State of the room the agent is currently in ( dirty / clean ) 
 * Potential Actions : Suck dirt , Stay idle , Move (CW , CCW ). 
*/   
	if percept[current_room].isdirty then
		SD 
		return CW// Direction is arbitrary 
	return CW		
	    
```

**Why the problem is trivial and further explanation** : Since the performance measure is based solely on the number of clean rooms at the end of 11 actions , we can begin at any arbitrary room and exhaustively go through every room and clean them . Since the worst case cost *( every room including the starting room being dirty )*  is 11 actions then this simple snippet of code will be considered rational when examined utilizing the performance measure  . 

**b) The reason why this agent is rational because:**
- It prioritizes cleaning dirty rooms immediately when encountered
- Since the performance measure is solely contingent on the number of rooms  after 11 actions  , we only concern ourselves with moving and cleaning at any chance we get as in the worst case scenario ( 11 actions ) all rooms will be clean regardless of whether we chose to rotate clockwise or counter clockwise . 
- It continues moving when no immediate dirty rooms are found, ensuring complete coverage

**c) How would the answer change (design and explanation) if the performance measure was applied from the initial moment?**  When the performance measure is applied at the initial moment the direction no longer is arbitrary.  We must now tailor the design of our agent so that we minimize the sum of the current performance measures over the course of 11 actions . We can represent this relation between steps taken and the performance measure as a summation . 

$$\sum_{t=0}^{11} F(t)$$

where $F(t)$ represents the number of clean rooms at time step $t$. For a 6-room environment, $0 \leq F(t) \leq 6$ at any time $t$. Our new algorithm is can be implemented as follows ...

```c
function SIMPLE_REFLEX_INITIAL_MOMENT_AGENT(percept) 
/* INPUT : ( percepts ) the current room the agent is in and the status of the    * rooms . 
 * STATE : Current State of the room the agent is currently in ( dirty / clean ) 
 * Potential Actions : Suck dirt , Stay idle , Move (CW , CCW ). 
*/   
	if percept[current_room].isdirty then
        return SD
    
    // If current room is clean, look at immediate neighbors
    next_CW = (current_room_number + 1) MOD 6
    next_CCW = (current_room_number - 1 + 6) MOD 6
    
    // Move to dirty neighbor if one exists
	if percept[next_CW].isDirty then
        return CW
    IF percept[next_CCW].isDirty then  
        return CCW
    
    return SI  // Stay idle if current and neighboring rooms are clean
```

**d) With  the possibility of incurring penalties :**

```c
function PENALTY_AWARE_REFLEX_AGENT(percept) 
/* INPUT : ( percepts ) the current room the agent is in and the status of the    * rooms . 
 * STATE : Current State of the room the agent is currently in ( dirty / clean ) 
 * Potential Actions : Suck dirt , Stay idle , Move (CW , CCW ). 
*/   
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
    if percept[current_room_status].isDirty THEN
        RETURN SD
    
    // Simple clockwise exploration since we can't see other rooms
    RETURN CW  // Always move clockwise when in clean room
```

Motivation:
Cannot optimize movement direction since neighbouring rooms are not visible . The agent uses consistent clockwise movements to ensure eventual complete coverage of all the rooms . The reason why this strategy is rational because the agent immediately cleans dirty rooms when found , systematically moves to the next room to pattern prevent getting stuck and will eventually visit all rooms in the circular environment. Since we are constrained by agent's limited knowledge we cannot make a more informed decision of how to proceed . On the bright side the reduction in sensor capability simplifies our agent's decision-making process .

# Exercise 2 

### **a) Rational Agent Design** 

I've decided to implement the agent within the pseudocode utilizing an agent object . 

#### Pseudocode 

```c
CLASS SimpleReflexVacuumAgent:
    function Initialize():
        currentPosition = [0,0]  
        movementPattern = ["right", "down", "left", "up"]
        currentMoveIndex = 0

    function GetAction():
        action = "SD"  
        
        nextMove = movementPattern[currentMoveIndex]
        currentMoveIndex = (currentMoveIndex + 1) MOD 4
        
        if nextMove = "right" AND currentPosition[1] < 1 then 
            currentPosition[1] = currentPosition[1] + 1
        ELSE IF nextMove = "left" AND currentPosition[1] > 0 THEN
            currentPosition[1] = currentPosition[1] - 1
        ELSE IF nextMove = "down" AND currentPosition[0] < 1 THEN
            currentPosition[0] = currentPosition[0] + 1
        ELSE IF nextMove = "up" AND currentPosition[0] > 0 THEN
            currentPosition[0] = currentPosition[0] - 1
        END IF
        
        RETURN action

    function IsValidMove(move):
        IF move = "right" THEN
            RETURN currentPosition[1] < 1
        ELSE IF move = "left" THEN
            RETURN currentPosition[1] > 0
        ELSE IF move = "down" THEN
            RETURN currentPosition[0] < 1
        ELSE IF move = "up" THEN
            RETURN currentPosition[0] > 0
        END IF
        RETURN FALSE
```

#### Function Signature Explanations 

```c
void Initialize() :
```

Utilized to initialize the agent , since our starting room is arbitrary , I've decided to place the agent in the top left room [0,0] . As per the specifications , the agent is allowed four valid moves : left , right , up , down . Also I've initialized a member variable to represent the current move index . 

```c
action GetAction():
```

This function utilizes the current position to derive the where the agent should travel next . It also increments the CurrentMoveIndex  and mods it so that it remains within logical bounds of what can be considered a valid move . 