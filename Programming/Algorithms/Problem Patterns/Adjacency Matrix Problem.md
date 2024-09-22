Given an undirected graph G=(V,E), the augmented graph $G^A=(V,E^A)$ is defined such that $uv$ is in E^A if and only if $uv ∉ E$ and there is a vertex w such that $uw$ is in E and $vw$ is in E.

Design efficient algorithms for computing G^A from G for both the adjacency-list

#### Suppose $G = \{(A, B), (B, C), (B, D), (C, D), (D, E)\}$
---
**Step One** : Iterate through the adjacency list . If    


```c
Algorithm ComputeAugmentedGraph(G):
    Input: G - an undirected graph represented as an adjacency list
    Output: G_A - the augmented graph G^A

    V = number of vertices in G
    G_A = new adjacency list of size V, initialized with empty sets

    for u = 0 to V-1 do
        for v = u+1 to V-1 do
            if v is not in G[u] then  // u and v are not connected in G
                for each w in G[u] do
                    if w is in G[v] then
                        // Found a common neighbor, add edge to G^A
                        Add v to G_A[u]
                        Add u to G_A[v]
                        break  
                    end if
                end for
            end if
        end for
    end for

    return G_A
End Algorithm

```
 ___ 
 Tags : #programming #algorithms 