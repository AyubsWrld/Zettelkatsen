___
Tags : #ai
____

What is the Initial State as it relates to games ? ;; Board configuration at a starting point 

What is the Successor function as it relates to games ? ;; list of tuples ( move , state ) representing legal moves . 

What is a Terminal Test as it relates to games ? ;; Is the game finished ? 

What is the Utility Function as it relates to games ? ;; Gives numerical value of terminal state ( +1 : win ) , ( -1 : loss ) and ( 0 : draw ) . 

What is Minimax ? ;; Algorithm within game theory wherein two plays who play optimally try to gain an edge over the other through maximizing/minimizing the other players outcome . 

What happens if one of the players within minimax does not play optimally , lets say the min player ? ;; It would be even better for the opposing player .


Minimax Pseudocode ? ;; ![[Pasted image 20250306143215.png]]
Is Minimax complete ? ;; Yes , if the tree is finite 
Is minimax optimal ? ;; Yes , against optimal opponent

What is the time complexity of minimax ? $O(b^m)$
What is the space complexity of minimax ? $0(bm)$

Apply Minimax to this tree : ![[Pasted image 20250306143510.png]] ;;![[Pasted image 20250306143718.png]]

What is the main problem with minimax search , How can we combat this ? ;; Number of game states is exponential to the number of moves . We can utilize alpha beta pruning to combat this . 


What is Alpha in Alpha-beta pruning ? ;; The value of the best choice we have found so far for max 

What is beta in Alpha beta pruning ? ;; The value of the best choice we have found so far for min . 

What is Alpha-beta pruning ? ;; Optimization technique utilized within minimax search to decrease the number of nodes which need to be explored . 


How does Alpha beta pruning work ? ;; if 



