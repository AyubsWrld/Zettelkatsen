- Run two simultaneous searches
	- One forward from the initial state
	- One backward from the goal 

- *Complete* ? Yes , if b is finite and both directions use breadth first 
- *Time* ? $\mathbb{O}(b^{\dfrac{d}{2}})$
- *Space* ? Same as time
- *Optimal* ? Yes, if step cost is one 

#### Special Requirements : 
- For searching backwards - predecessor function - must be easily computable 
- Explicit definition of the goal state(s)
______

Tags : #programming #artificial-intelligence