___
Tags : #ai
____

What is *Local Search* ?;;Finding solutions to optimization problems by iteratively exploring the search space.
<!--SR:!2025-03-05,1,230-->

What is a Neighboring State ?;; The state that can be reached from a current state with minimal change  ( ===Valid move=== ) .
<!--SR:!2025-03-05,1,230-->

What is Local Maxima/Optima ? ;; Local Search can often get stuck in ===Local Maxima=== where it cannot improve the solution via any neighboring states.
<!--SR:!2025-03-05,1,230-->

Hill-climbing ;; Loop which continues and improves in an ascending fashion .
<!--SR:!2025-03-05,1,230-->

Hill-Climbing Pseudo Code;;![[Pasted image 20250304211518.png]]
<!--SR:!2025-03-06,2,243-->

When is Local Search the ideal solution ? ;; When the search space is expansive and we there are obvious memory constraints 

How can we solve ===Local Maxima== problem ? ;; through the use of ===Simulated Annealing===

What is Simulated Annealing? ;; ===Probabilistic solution=== which occasionally moves to worse solutions to escape local optima 

What is Genetic Algorithm ? ;; Combining components of optimal solutions to produce a new , potentially optimized solution . 

How does Genetic Algorithm select parents ? ;; Through finding the best fit parents based off a heuristic function . 

What is Stochastic Hill-Climbing ? ;; Another ===Probabilistic Solution=== to dealing with ===Local Maxima=== , The choice of a neighbor selected is randomized as opposed to always choosing the most optimal solution . 

How does Stochastic Hill-Climbing work ? ;; Start with an initial solution $\rightarrow$ Evaluate the current solutions fitness ( Using a heuristic function ) $\rightarrow$ Select a random neighbor $\rightarrow$ If the new solution is better than the current one we move to it , otherwise we stay at the current solution . 

What is Random Restart Hill-Climbing ? ;; Hill-climbing search that runs multiple different times with different initial states . 

:LiQuestionMarkGlyph: What is Local Beam Search ? ;; Similar to Local Search however we explore $k$ candidates as opposed to a singular current state exploring neighbors . We kill off 