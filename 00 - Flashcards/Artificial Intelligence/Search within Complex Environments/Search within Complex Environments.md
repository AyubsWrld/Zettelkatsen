___
Tags : #ai
____

What is *Local Search* ?;;Finding solutions to optimization problems by iteratively exploring the search space.
<!--SR:!2025-03-07,1,190-->

What is a Neighboring State ?;; The state that can be reached from a current state with minimal change  ( ===Valid move=== ) .
<!--SR:!2025-03-07,2,230-->

What is Local Maxima/Optima ? ;; Local Search can often get stuck in ===Local Maxima=== where it cannot improve the solution via any neighboring states.
<!--SR:!2025-03-07,1,190-->

Hill-climbing ;; Loop which continues and improves in an ascending fashion .
<!--SR:!2025-03-07,1,190-->

Hill-Climbing Pseudo Code;;![[Pasted image 20250304211518.png]]
<!--SR:!2025-03-11,5,243-->

When is Local Search the ideal solution ? ;; When the search space is expansive and we there are obvious memory constraints
<!--SR:!2025-03-07,2,243-->

How can we solve ===Local Maxima== problem ? ;; through the use of ===Simulated Annealing===
<!--SR:!2025-03-07,1,203-->

What is Simulated Annealing? ;; ===Probabilistic solution=== which occasionally moves to worse solutions to escape local optima
<!--SR:!2025-03-07,1,203-->

What is Genetic Algorithm ? ;; Combining components of optimal solutions to produce a new , potentially optimized solution .
<!--SR:!2025-03-07,1,203-->

How does Genetic Algorithm select parents ? ;; Through finding the best fit parents based off a heuristic function .
<!--SR:!2025-03-07,2,243-->

What is Stochastic Hill-Climbing ? ;; Another ===Probabilistic Solution=== to dealing with ===Local Maxima=== , The choice of a neighbor selected is randomized as opposed to always choosing the most optimal solution .
<!--SR:!2025-03-07,1,203-->

How does Stochastic Hill-Climbing work ? ;; Start with an initial solution $\rightarrow$ Evaluate the current solutions fitness ( Using a heuristic function ) $\rightarrow$ Select a random neighbor $\rightarrow$ If the new solution is better than the current one we move to it , otherwise we stay at the current solution .
<!--SR:!2025-03-07,1,203-->

What is Random Restart Hill-Climbing ? ;; Hill-climbing search that runs multiple different times with different initial states .
<!--SR:!2025-03-07,1,203-->

:LiQuestionMarkGlyph: What is Local Beam Search ? ;; Similar to Local Search however we explore $k$ candidates as opposed to a singular current state exploring neighbors . We kill off
<!--SR:!2025-03-07,2,243-->

What is an AND-OR tree ? ;; A Graphical representation of a Non-deterministic state space wherein OR nodes delineate a choice an Agent needs to make at a certain time and AND nodes which represent the set of all states present at a given time .
<!--SR:!2025-03-07,1,215-->

What is Backtracking? ;; A problem solving approach wherein a sequence of steps are stored in memory and if the agent arrives at a dead end they may return to a previous state .
<!--SR:!2025-03-07,1,215-->

What is Belief State Space ? ;; The set of _potential_ states which follow an action .
<!--SR:!2025-03-07,1,215-->

What is the Long Walk Problem? ;; The long walk problem is a flaw within ===Online DF-search === wherein the agent spends time traversing a path which is close to the solution but is irrelevant to getting the agent any closer to the real solution .
<!--SR:!2025-03-07,1,215-->

