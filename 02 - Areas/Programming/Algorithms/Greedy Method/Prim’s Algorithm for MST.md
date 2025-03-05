Prim’s algorithm is a **greedy algorithm** used to find the **Minimum Spanning Tree (MST)** of a weighted, connected, and undirected graph. Let's go through the pseudocode step-by-step and explain what it does in simpler terms:

---

### **Pseudocode Breakdown**

#### 1. **Initialization**

- **`MST-Prim(G, W, r)`**:
    
    - The function starts with three inputs:
        - **`G`**: The graph, containing vertices and edges.
        - **`W`**: The weights of the edges in the graph.
        - **`r`**: The starting vertex (any vertex can be chosen).
- **`Q = V[G]`**:
    
    - A **priority queue (`Q`)** is initialized with all vertices of the graph `G`. The queue is used to keep track of vertices that have not yet been added to the MST.
- **`for each u ∈ Q`**:
    
    - For each vertex `u` in the graph:
        - **`key[u] = ∞`**: Set the initial cost (key) to include this vertex in the MST as infinity. This is because we haven’t calculated the actual weights of the edges yet.
        - **`key[r] = 0`**: Set the cost (key) of the starting vertex `r` to `0`. This ensures the algorithm starts by adding the starting vertex to the MST.
- **`p[r] = NULL`**:
    
    - The **parent (`p[r]`)** of the starting vertex is set to `NULL` because it has no parent—it’s the first vertex in the MST.

---

#### 2. **Main Loop**

- **`while (Q not empty)`**:
    - As long as there are vertices in the queue `Q`, the algorithm keeps running.
        
    - **`u = ExtractMin(Q)`**:
        
        - Find the vertex `u` in the queue `Q` with the smallest key value (i.e., the least cost to add it to the MST).
        - Remove this vertex `u` from `Q`. This vertex is now part of the MST.
    - **`for each v ∈ Adj[u]`**:
        
        - Check all vertices `v` that are directly connected to `u` (its neighbors).
            
        - **`if (v ∈ Q and W(u, v) < key[v])`**:
            
            - Check two conditions:
                1. Vertex `v` is still in the queue `Q` (i.e., it hasn’t been added to the MST yet).
                2. The weight of the edge `(u, v)` is less than the current key value of `v`.
            - If both conditions are true:
                - **`p[v] = u`**:
                    - Update the parent of `v` to `u`. This means that the edge `(u, v)` will be part of the MST.
                - **`key[v] = W(u, v)`**:
                    - Update the key of `v` to reflect the weight of the edge `(u, v)`. This ensures that the least-cost edge is selected for the MST.

---

#### 3. **Completion**

- When the priority queue `Q` is empty, all vertices have been added to the MST.
- The MST is represented by the array **`p`**, which stores the parent of each vertex. By following the `p` array, you can reconstruct the MST.

---

### **Simplified Example**

Let’s consider an example graph:

| Edge | Weight |
| ---- | ------ |
| A-B  | 4      |
| A-C  | 2      |
| B-C  | 3      |
| B-D  | 5      |
| C-D  | 1      |

**Step-by-Step Execution**:

1. Start with vertex `A` (`r = A`).
    - `key[A] = 0`, `key[B] = ∞`, `key[C] = ∞`, `key[D] = ∞`.
2. Extract `A` (key = 0) from `Q`.
    - Update neighbors:
        - For `B`: `key[B] = 4`, `p[B] = A`.
        - For `C`: `key[C] = 2`, `p[C] = A`.
3. Extract `C` (key = 2) from `Q`.
    - Update neighbors:
        - For `D`: `key[D] = 1`, `p[D] = C`.
4. Extract `D` (key = 1) from `Q`.
    - No updates (remaining edges are not cheaper).
5. Extract `B` (key = 4) from `Q`.

MST: `{A-C, C-D, A-B}` with total weight = 2+1+4=72 + 1 + 4 = 7.

---

### **Time Complexity**

1. **Using a priority queue**:
    - Extracting the minimum: O(log⁡V)O(\log V) for each of VV vertices.
    - Updating keys: O(log⁡V)O(\log V) for each of EE edges.
    - **Overall Complexity**: O(Elog⁡V)O(E \log V), where EE is the number of edges and VV is the number of vertices.

Prim's algorithm is efficient and widely used for finding MSTs in practical applications.
 ___
 Tags : #programming #algorithms 