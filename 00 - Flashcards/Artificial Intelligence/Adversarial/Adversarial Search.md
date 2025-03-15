___
Tags : #ai
____

What is the Initial State as it relates to games ? ;; Board configuration at a starting point
<!--SR:!2025-03-15,1,225-->

What is the Successor function as it relates to games ? ;; list of tuples ( move , state ) representing legal moves .
<!--SR:!2025-03-15,1,225-->

What is a Terminal Test as it relates to games ? ;; Is the game finished ?
<!--SR:!2025-03-15,1,225-->

What is the Utility Function as it relates to games ? ;; Gives numerical value of terminal state ( +1 : win ) , ( -1 : loss ) and ( 0 : draw ) .
<!--SR:!2025-03-15,1,225-->

What is Minimax ? ;; Algorithm within game theory wherein two players who play optimally try to gain an edge over the other through maximizing/minimizing the other players outcome .
<!--SR:!2025-03-16,2,245-->

What happens if one of the players within minimax does not play optimally , lets say the min player ? ;; It would be even better for the opposing player .
<!--SR:!2025-03-16,3,250-->


Minimax Pseudocode ? ;; ![[Pasted image 20250306143215.png]]
<!--SR:!2025-03-15,1,225-->
Is Minimax complete ? ;; Yes , if the tree is finite
<!--SR:!2025-03-15,1,225-->
Is minimax optimal ? ;; Yes , against optimal opponent
<!--SR:!2025-03-16,2,230-->

What is the time complexity of minimax ? $O(b^m)$
What is the space complexity of minimax ? $0(bm)$

Apply Minimax to this tree : ![[Pasted image 20250306143510.png]] ;;![[Pasted image 20250306143718.png]]
<!--SR:!2025-03-15,1,225-->

What is the main problem with minimax search , How can we combat this ? ;; Number of game states is exponential to the number of moves . We can utilize alpha beta pruning to combat this .
<!--SR:!2025-03-15,1,225-->


What is Alpha in Alpha-beta pruning ? ;; The value of the best choice we have found so far for max
<!--SR:!2025-03-15,1,225-->

What is beta in Alpha beta pruning ? ;; The value of the best choice we have found so far for min .
<!--SR:!2025-03-16,2,230-->

What is Alpha-beta pruning ? ;; Optimization technique utilized within minimax search to decrease the number of nodes which need to be explored .
<!--SR:!2025-03-15,1,225-->


How does Alpha beta pruning work ? ;; It eliminates branches in a game tree that cannot influence the final decision, improving efficiency by avoiding unnecessary evaluations.
<!--SR:!2025-03-15,1,210-->


What is Adversarial Search ? ;; It is a type of search wherein multiple players play against one another.
<!--SR:!2025-03-15,1,225-->

What is Monte Carlo Search ? ;; Monte Carlo Search is an approach wherein, given a current position , we allow the agent to run multiple simulations and select the best average outcome of those simulations.
<!--SR:!2025-03-15,1,225-->

What are the steps of Monte Carlo Search ? ;; Selection , Expansion , Simulation , Back-propagation.
<!--SR:!2025-03-15,1,225-->


What is a rollout policy with respect to MCTS ? ;; It is a strategy used to simulate the outcome of a game from a given state. It determines how moves are chosen when running simulations ( or "rollouts" ). 

What is selection policy with respect to MCTS ? ;; The selection policy helps navigate the search tree efficiently, focusing on promising moves while still exploring less-visited ones.


Why is the selection policy important ? ;; It helps balance exploration ( traversing new nodes ) with exploitation ( traversing nodes which we have already traversed in the past which are reliable ). 

What is exploration ? ;; The process of MCTS exploring new nodes within the tree 

What is exploitation ? ;; the process of exploring nodes which have already been proven to work well in moving us towards our goal. 

What is the UBC1 ? ;; Upper Confidence Bound is a the main formula which aids in the selecting which node to visit next. 

What is the $w_i$ in Upper Confidence Bound ?;; number of wins from this node. 

What is $n_i$ in Upper Confidence Bound ? ;; Number of times this node has been visited.

What is $N$ in Upper Confidence Bound ? ;; Total visits of the parent node. 

What is $C$ in Upper Confidence Bound? ;; Exploration constant often set to $\sqrt{2}$

What is the formula for Upper Confidence Bound ? ;; $$UCB1 = \dfrac{w_i}{n_i} + C \sqrt{\dfrac{ln \ N}{n_i}}$$
What is the process in MCTS ? ;; Start at the root of the tree -> Select the child node with the highest UCB1 score -> repeat until reaching a leaf node -> Expand a new node and run a rollout policy to estimate its value -> Backpropagate results to update values in the tree
