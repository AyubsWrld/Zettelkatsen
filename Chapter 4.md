#### N - Queens problem 
___
Sometimes the solution matters more than how we got there . The solution in this case is the final configuration of the Queens . 
#### Hill Climbing 
___
Start at a random point and see if its the highest . Downside of this is that you might find yourself at a local maxima when there's a larger hill somewhere else . **Move uphill** rule causes it to fail . 

Solved using ... 
- **Simulated annealing** : allow the AI to make a potentially bad move . Randomize ? 
- **Local Bean Search** : multiple AI agents looking at different parts for the solution -> drawback is groupthink . If all the agents start with similar solutions they all may converge at the same local maxima . We have to make sure that they are all searching different parts . 

#### Genetic Algorithms 
___
- Selection of the most "Fit" solution at any given time 
- Usually based on a heuristic 
- In the *N-queens* problem , the heuristic/fitness would be how many queens are place properly . We would only then select the ones that are in the best position . 
- With the best solutions we crossover and then sometimes they have better solutions 
- At some point the solutions resemble each other too quickly so we add a random mutation . 

#### Erratic Vacuum 
---
Non-deterministic action -> drops some dirt when its cleaning . AI needs to plan for contingencies and plan for all the outcomes . 


#### Any-or search tree
---
Uncertainty in action vs Uncertainty in Environment 
- ND node : Decision needs to be made , Trying to find guaranteed win with all the choices 
- Or node  : 
- Belief state : A single state that the AI might be in . 

#### Online Search
---
- Learn and act at the same time . 
- Balance exploration and exploitation . 
- Right balance between learning and traversing . Constantly updates its knowledge when it searches . 
- Adversary argument : NO fool-proof way of preventing dead-ends . 
#### Offline Search
---
- Planning in advance . 

#### LRTA 
___
Heuristic Isn't fixed . Starts with an estimate and refines estimate . 