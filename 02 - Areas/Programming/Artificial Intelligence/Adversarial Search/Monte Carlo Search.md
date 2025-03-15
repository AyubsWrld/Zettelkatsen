Monte Carlo Search is an approach that allows the agent to run multiple different simulations from a current and position and select the best move based on these games.

##### Monte Carlo Search runs four main steps 
- **Selection** : based on the current position select the most promising node.
- **Expansion** : Add possible moves ( children ) for the current position. 
- **Simulation**: Running a random playout to see what might happen if we take a certain move. 
- **Back-propagation** : Utilize the results of the simulation to update the value of previous moves. 

#### Analogy 
___
Imagine your playing the same Fiora vs. Renekton lane again. You understand that you would play better against this matchup the more games you have played , and based on these games you can deduce what the optimal way to play the matchup is.
______

Tags : #programming #artificial-intelligence
