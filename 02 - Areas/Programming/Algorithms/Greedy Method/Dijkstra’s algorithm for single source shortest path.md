Used to find the shortest path to every vertex within a graph ( Can be directed or undirected ) . This usually involves 3 steps … 
1. `Setup` : We are given a graph and instructed to find the shortest path to every point within the graph from a starting point  within the graph . Firstly we start by setting the source paths distance to zero , then we set all the other vertices' within the graph to infinity . Lastly we initialize an empty priority queue . 
2. `Explore` : We then add all of the nodes adjacent to our starting point to the priority queue ( Note that the priority queue's constraint is that the top node has the lowest distance ) . After that we pop the vertex with the shortest distance as use that as our node of interest `v*` . In every step we check whether we can relax or not .  The relaxation occurs when we have `d[v]` + `c(u,v)` < `d[u]` . 
3. `Return home` : After all the distances have been calculated ( )
 ___
 Tags : #programming #algorithms 