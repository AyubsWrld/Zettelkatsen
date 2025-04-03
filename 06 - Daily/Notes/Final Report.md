## Minimax Search Agent: Logan Paillard, Eric Persa, Dan Eze, Ayub Mohamed 
## CMPT 355 
## Mar 20, 2025 
## Course Instructor Name: Dr. Calin Anton
## 1. Introduction

Our goal was to implement an optimized adversarial search agent capable of effectively playing the Tukvnanawopi board game. To aid in accomplishing this goal we implemented an instance of the Minimax algorithm which utilizes Alpha-beta pruning in conjunction with a carefully crafted evaluation function for optimization. This report serves as an explanation of the rationale behind our design choices, our implementation of the Minimax algorithm, any optimizations we applied to aid in performance, and all of the challenges we faced along the way.

## 2. Rationale Behind Selection

When selecting an algorithm for the Tukvnanawopi board game, we considered both Minimax with Alpha-Beta pruning and Monte Carlo Tree Search (MCTS). Several factors where weighed in our final decision in going with Minimax:

### Deterministic Nature of Tukvnanawopi

The most notable factor during our selection of the algorithm was the deterministic nature of Tukvnanawopi. Given the lack of both hidden elements and randomness within the environment, Minimax guarantees optimal play, whereas MCTS offered a more probabilistic result based on a series of randomly generated playouts. Since we faced no significant computational constraints, we chose to go with Minimax as we believed that it would be the ideal choice under the given conditions.

### Branching Factor Considerations

The branching factor was another key consideration we made during our algorithm selection. A problem which we knew we would face during our implementation was Tukvnanawopi's sizeable branching factor. However, after careful consideration, we concluded that the branching factor would remain manageable for Minimax if counteracted with Alpha-Beta pruning. In doing so, we would be able to significantly reduce the search space, making our implementation computationally feasible within the allotted time constraints.

### Evaluation Function Effectiveness

Given our confidence in designing an effective evaluation function that accurately captures the game state, Minimax became particularly attractive to us. The clear metrics for generating and assigning heuristic values (piece count, mobility, and capture potential) allowed us to create an evaluation function that accurately reflected the game state at any point of the overarching game loop, which is essential for Minimax and enabled us to implement a more aggressive Alpha-Beta pruning procedure.

### Implementation Simplicity and Time Constraints

The straightforward implementation path offered by Minimax, given the project's time constraints compared to MCTS—which would have required complex simulations and carefully balancing exploration/exploitation phases—was another factor in our choice of algorithm selection. Given these considerations, we chose to go with Minimax in the implementation of our search agent.

## 3. Code Appendices

The following appendices provide a high-level overview of our Minimax algorithm, Alpha-beta pruning technique, and evaluation function. Each appendix includes a language-agnostic representation of the code, followed by an implementation in the Python programming language.


### $\text{Appendix I}:$ Minimax Algorithm & Pruning Procedure
1. Signature: `bool minimax(self, node , depth, maximizing_player)`
2. Parameters: 
	1. `node`: Node object representing the child node to be passed down recursively from parent to child. 
	2. `depth`: Integer representing the current depth of the node.
	3. `maximizing_player`: Boolean representing whether the current player is maximizing or minimizing.  
	4. `alpha`: Float representing of the best value found so far for the maximizing player. Serves to represent the lower bound of possible outcomes for the maximizing player, any value lower than this can be safely pruned.
	5. `beta`: Float representing the best value found so far for the minimizing player. Serves to represents the upper bound of possible outcomes for the minimizing player, any value greater than `beta` can be safely pruned.
3. Purpose: The algorithm traverses possible game states in order to find the best move for a given player ( either the maximizing player or minimizing player ).
4. Algorithm Logic:
    - Begin by checking if the game is in a terminal state or if the maximum depth has been reached, if so return the evaluation score.
    - Conduct a key comparison on `maximizing_player` to derive whether we are the maximizing player or the minimizing player. 
    - If we are the maximizing player (white): we select the move that would result in the highest evaluation score.
    - If the preceding case is false it implies that we are the minimizing player (black): Choose the move that leads to the lowest evaluation score.
    - Alpha-beta pruning, which an in depth explanation is provided in $\text{Appendix II}$ , is then used to reduce the number of nodes evaluated.
5. Key Components:
    - The `is_terminal` function determines if the game is in a terminal state by
	    - A calculation of the number of pieces remaining for both players followed by a key comparison to determine the whether that number is equivalent to zero signifying the conclusion of the game. 
	    - Calculating whether each player has any valid moves. 
    - `node.possible_states()` generates all possible next states from the current position.
    - The algorithm recursively evaluates child nodes, alternating between maximizing and minimizing players.
    - If a branch is found to be worse than a previously explored option, that branch is pruned.

#### Language Agnostic Representation 

```c
Function Minimax(state, depth, player, alpha, beta) = 
    if state is terminal or depth = 0:
        return evaluation(state)
    if player is maximizing:
        return max(Minimax(child, depth-1, minimizing, alpha, beta)) for all child states
    else:
        return min(Minimax(child, depth-1, maximizing, alpha, beta)) for all child states
```

#### Corresponding Python Implementation 

```python 
    def minimax(self, node: Node, depth:int, maximizing_player: bool, alpha: float = -np.inf, beta: float = np.inf) -> int:
        if self.is_terminal(node.state, self.player):
            return self.utility(node), node.move
        if depth == 0:
            return self.evaluate(node), node.move

        if maximizing_player:
            max_eval = -math.inf
            best_move = None
            node.possible_states() # generate the children of the 
            for child in node.children:
                eval, _ = self.minimax(child, depth-1, False, alpha, beta) # call minimax for minimizing player
                if eval > max_eval:
                    max_eval = eval
                    best_move = child.move
                alpha = max(alpha, eval)
                if max_eval >= beta: #prune
                    break
            return max_eval, best_move
        else:
            min_eval = math.inf
            best_move = None
            node.possible_states() # generate the children of the 
            for child in node.children:
                eval, _ = self.minimax(child, depth-1, True, alpha, beta) # call minimax for minimizing player
                if eval < min_eval:
                    min_eval = eval
                    best_move = child.move
                beta = min(alpha, eval)
                if min_eval <= alpha: #prune
                    break
            return min_eval, best_move

    def is_terminal(self, state, player: Player) -> bool:
        white_pieces = np.count_nonzero(state == "W")
        black_pieces = np.count_nonzero(state == "B")


        if white_pieces == 0 or black_pieces == 0:
            return True

        has_valid_moves = False

        if player == "W":
            positions = np.where(state == "W")
        else:
            positions = np.where(state == "B")

        rows = positions[0]
        cols = positions[1]

        for i in range(len(rows)):
            row, col = rows[i], cols[i]

            directions = [
                (-2, 0), (2, 0), (0, -2), (0, 2),  
                (-1, -1), (-1, 1), (1, -1), (1, 1),  
            ]

            for dr, dc in directions:
                new_row, new_col = row + dr, col + dc
                if self.root.is_within_bounds(new_row, new_col, state) and state[new_row, new_col] == "O":
                    has_valid_moves = True
                    break

            if has_valid_moves:
                break

        # If current player has no valid moves, the game is also over
        return (white_pieces == 0 or black_pieces == 0 or not has_valid_moves)
```


### $\text{Appendix II}:$ Alpha Beta Pruning Procedure

1. Purpose: Used to eliminate branches of the search tree that would not have otherwise influenced the final decision, in doing so we significantly reduce computation time without affecting the result.
2. How It Works:
    - Alpha represents the minimum score that the maximizing player is assured of.
    - Beta represents the maximum score that the minimizing player is assured of.
    - If at any point within the search beta ≤ alpha, it is implied that the current player can't improve their situation by exploring further branches, so those branches are pruned.
3. Implementation Details:
    - The alpha and beta values are passed down through recursive calls and updated when a better move is found.
    - Whether pruning ensues or not is dependent on whether we are the minimizing or maximizing player and occurs as follows: when `max_eval >= beta` for maximizing player or `min_eval <= alpha` for minimizing player.
      
#### Language Agnostic Representation 

```c
if player is maximizing:  
    for each child in state.children:  
        value = Minimax(child, depth - 1, minimizing, alpha, beta)  
        if value > alpha:  
            alpha = value  
        if alpha ≥ beta:  // Prune the remaining branches  
            break  

else:  // Minimizing player  
    for each child in state.children:  
        value = Minimax(child, depth - 1, maximizing, alpha, beta)  
        if value < beta:  
            beta = value  
        if beta ≤ alpha:  // Prune the remaining branches  
            break  
```

#### Corresponding Python Implementation 

```python
if maximizing_player:
    for child in node.children:
        eval, _ = self.minimax(child, depth - 1, False, alpha, beta)
        alpha = max(alpha, eval)
        if alpha >= beta:  # Prune
            break

else:  # Minimizing player
    for child in node.children:
        eval, _ = self.minimax(child, depth - 1, True, alpha, beta)
        beta = min(beta, eval)
        if beta <= alpha:  # Prune
            break
```

### $\text{Appendix III}:$ Evaluation function 

1. Signature : `float evaluate(node)`
2. Purpose: Calculates and assigns a heuristic score for non-terminal game states to guide the search process.
3. Components:
    - Piece Count: The number of pieces each player has on the board, weighted at 0.6.
    - Move Availability: The number of possible moves for each player, weighted at 0.15.
    - Capture Potential: The number of captures each player can make, weighted at 0.25.
4. Scoring Mechanism:
    - The evaluation function computes a score for both the current player and the opponent upon which each factor (pieces, moves, captures) is multiplied by its respective weight. The final score is the difference between the player's score and the opponent's score.
    - A positive score indicates an advantage for the current player, while a negative score indicates an advantage for the opponent.
5. **Implementation Details**:
    - The function dynamically determines the opponent based on the current player.
    - It accesses node properties to gather information about piece counts, available moves, and potential captures.
    - The weighting system prioritizes maintaining more pieces on the board while still valuing tactical advantages like mobility and capture opportunities.
#### Language Agnostic Representation 

```c
Function Evaluate(node):

	//Determine the opponent
	
	If player is "B", opponent is "W"
	Otherwise, opponent is "B"

    //Count the number of pieces for both players:
    
	player_count = number of player's pieces in node's state
	opponent_count = number of opponent's pieces in node's state

	//Get the number of possible moves
	
	player_moves = node's available moves
	opponent_moves = sum of moves from all child nodes

	//Get the number of captured pieces
	
	player_captures = number of captures by the player in node
	opponent_captures = sum of captures from all child nodes

	//Assign weights to each factor
	
	piece_weight = 0.6
	move_weight = 0.15
	capture_weight = 0.25

	player_score = (player_count × piece_weight) + (player_moves × move_weight) + (player_captures × capture_weight)
	opponent_score = (opponent_count × piece_weight) + (opponent_moves × move_weight) + (opponent_captures × capture_weight)
	
Compute final score:
	total_score = player_score - opponent_score

Return total_score

```

#### Corresponding Python Implementation 

```python
def evaluate(self, node: Node) -> float:
    opponent = "W" if self.player == "B" else "B"

    player_count = np.count_nonzero(node.state == self.player)
    opponent_count = np.count_nonzero(node.state == opponent)

    player_moves = node.moves
    opponent_moves = sum(child.moves for child in node.children)

    player_captures = node.captures
    opponent_captures = sum(child.captures for child in node.children)

    # Assign weights to each factor
    piece_weight = 0.6
    move_weight = 0.15
    capture_weight = 0.25

    player_score = (player_count * piece_weight) + (player_moves * move_weight) + (player_captures * capture_weight)
    opponent_score = (opponent_count * piece_weight) + (opponent_moves * move_weight) + (opponent_captures * capture_weight)

    # Normalize between -1 and 1
    total_score = player_score - opponent_score

    return total_score

```

### 4. Challenges Faced

During our implementation of the Minimax algorithm with Alpha-beta pruning for the Tukvnanawopi game, we encountered several challenges that affected the performance of our implementation. One of the primary difficulties was the significant overhead in computation time, which was caused by the game's large branching factor. Our choice of Python as the implementation language also played a key role in this challenge. One of the challenges we knew we would eventually run into with utilizing Python was its handling of variables - specifically, that it passes variables by value rather than by reference. We were aware that we were required to pass our nodes between different functions, and the inability to pass by reference added another layer of overhead, particularly in recursive calls. Alpha-beta pruning alleviated some of the computational burden by reducing the number of nodes evaluated, ensuring that the pruning was optimally applied and avoiding redundant evaluations remained difficult. Another challenge was the design of the evaluation function. We needed to ensure that we retained a balance between its ability to accurately capture various aspects of the game (such as piece count, mobility, and capture potential) and being efficient enough to compute within the time constraints, as we knew we would be calling it often.

### 5. Potential Improvements

While our current implementation of the search agent is effective, there are several areas where improvements could potentially be made. One of the biggest optimizations we could make to improve the efficiency of our agent would be to port its implementation to a language where we are given access to the underlying memory model. In doing so, we would be able to carefully decide when and where in execution we would like to pass objects and how we would go about doing so (by reference or by value). 


### 6. Conclusion

To conclude, our endeavors to implement the Minimax algorithm with Alpha-beta pruning has proven to be a success. We were able fulfill our goal of creating a robust adversarial search agent capable of playing the Tukvnanawopi board game. Through our careful exploitation of the deterministic nature of the game and optimizing the search with Alpha beta pruning to deal with the branching factor, the agent was able to make rational decisions in a reasonable amount of time. While there are most certainly areas we could improve with respect to optimization and refinement of the algorithm, particularly in the evaluation function and search depth, the current design provides a robust foundation for the game's AI if we ever desire to refine it further. 