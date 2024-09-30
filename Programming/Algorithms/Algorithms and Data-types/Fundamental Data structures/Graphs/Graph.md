Composed of edges  , $E$ ,  and Vertices  , $V$   . Edges represent relationships between vertices . When two vertices , $Y , E$  are connected ,   $Y$ is said to be adjacent to $E$ .  When the graph is directed we have a concept of $In$ neighbours and $Out$ neighbours . 

##### Some things to keep in mind 
____
*Number of edges n = (|N|)* 
*Number of  Vertices m = (|M|)*  

**Graphs may also have weight**
**Complete Graphs have all edges connecting all vertices , m = n(n-1)/2** 

##### Types of graphs
___
 - *Acyclic Graph* : A graph with no cycles , that is once there is every vertex is adjacent to at most one neighbour . 
 - *Subgraph* :   Given two graphs , $G_1 , G_2$ , for every edge $E \in G_1 , E \in G_2$   . However not all vertices must be present in $G_1$ . Then $G_1$ is said to be a subgraph of $G_2$ . 
 - *Induced Subgraph* :   Every edge and vertex exists .
-  *Disconnected Graph* : A graph which is comprised of multiple parts . 
#####  Representing a graph 
___
**Adjacency matrix** :  
$$ m=
\begin{bmatrix} 
	0 & 1 & 1 \\
	1 & 0 & 1\\
	1 & 1 & 0 \\
	\end{bmatrix}
$$
*1* implies edge exists , $0$ implies that edge does not . 
*A digraph is asymmetric across the diagonal whereas a undirected graph is symmetric* .

Within a weighted graph , the weights are substituted for the ones , $0$ is a valid weight , so if the edge does not exist it is infinite .

$$ m=
\begin{bmatrix} 
	\infty & 3 & 5 \\
	1 & \infty & 1\\
	1 & 0 & \infty \\
	\end{bmatrix}
$$

A *complete graph* has all ones filled in 
$$ m=
\begin{bmatrix} 
	0 & 1 & 1 \\
	1 & 0 & 1\\
	1 & 1 & 0 \\
	\end{bmatrix}
$$

A *disconnected graph* has a zero in its column and row
$$ m=
\begin{bmatrix} 
	0 & 0 & 0 \\
	1 & 0 & 0\\
	1 & 1 & 0 \\
	\end{bmatrix}
$$

____
Tags : #algorithms  #graphs