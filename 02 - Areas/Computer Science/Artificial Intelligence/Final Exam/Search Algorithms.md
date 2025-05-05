### **I. Uninformed Search**

1. **Breadth-First Search (BFS)** :
	 Uses Queue to explore level by level. Complete if search Space is finite. Optimal if all step costs are equal. Time complexity $O(b^d)$ 
2. **Depth-First Search (DFS)**
	 Uses stack to explore until depth is reached . Not complete if there are any infinite paths. Unoptimal if the node it happens to traverse is deep 
3. **Uniform-Cost Search**
	BFS but instead utilizes priority queue to go the node with the lowest cost to get there. Is complete if search space is finite and is optimal in gauranteeing the lowest search cost. You want to use it when the weights are not uniform 
    
4. **Depth-Limited Search**
	Depth first search but limits the depth on how far it can traverse down the tree. Optimal? No , Complete? Yes if the solution is within the depth. 
    
5. **Iterative Deepening Search (IDS)**
    
6. **Bidirectional Search**
    

---

### **II. Informed (Heuristic) Search**

7. **Greedy Best-First Search**
   Uniform-Cost - step cost. Unoptimal and reliant on heauristic function. 
    
8. **A* Search**
	Uniform-Cost search + Heuristic. f(n) = g(n) + h(n).
    

---

### **III. Beyond Classical Search (Local Search & Nondeterminism)**

9. **Hill-Climbing**
	Utilizes while loop to gradually ascend in greatest order. 
    
10. **Simulated Annealing**
    
11. **Local Beam Search**
    
12. **Genetic Algorithms**
    
13. **AND-OR Search Trees**
    
14. **Online Search Agents**
---

### **IV. Adversarial Search**

15. **Minimax Search**
    
16. **Alpha-Beta Pruning**
    

---

### **V. Logical Inference as Search**

17. **Backward Chaining**
	 Solution -> Facts .

18. **DPLL Algorithm** (for SAT)
    
19. **Forward Chaining**
	  Facts -> Solution.
    
20. **Resolution**
    

---

### **VI. Knowledge Representation (as Search)**

21. **Semantic Network Search** (involves graph-based search methods)
    

---

### **VII. Learning-Based Search (ILP)**

22. **Inductive Logic Programming (ILP)**  
     • Example method: **FOIL** (First Order Inductive Learner)
    

---

### **VIII. Reinforcement Learning (Search over Policies or Utilities)**

23. **Passive Reinforcement Learning**
    
24. **Active Reinforcement Learning**
    
25. **Policy Search**