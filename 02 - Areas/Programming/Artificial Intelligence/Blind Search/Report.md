# **Air Berlin Puzzle Sort**
### Authors:  Dusan Barudzija, Dan, Ayub
#### CMPT 355
#### Jan 22, 2025

#### Course Instructor Name: Dr. Calin Anton

# 1. Search Algorithm

The chosen search algorithm we decided to implement to solve the AB puzzle Best-First Search . This approach is well suited for this problem because it prioritizes exploring the states which have the best chance of producing the desired end result . As a side effect of this approach , the algorithm removes the chance of expanding unnecessary branches which wil aid in reducing the size of the search tree all while retaining optimality and correctness. With every step , the current state is evaluated using a heuristic function, which calculates the Hamming-Distance between the current state and the known goal state and assigning a heuristic value to the node . By always expanding the state with the largest  heuristic value, the algorithm minimizes redundant exploration.

# 2. Evaluation Function 

As previously mentioned , The evaluation function is designed to aid in the search by calculating the Hamming-Distance between the current state and the desired goal state . The heuristic used is:

$$H(state) = \sum_{i=1}^{n^2}F(a_i \ ,b_i)$$

Wherein $n^2$ is the number of small disks , $a_i$ is the $i$-th element of the current state , $b_i$ is the $i$-th element of the desired result , and $F(a_i , b_i)$ is an indicator function which resolves to either of two scenarios . 

$$
F(a_i, b_i) =
\begin{cases} 
1, & \text{if } a_i \notin b_i \text{ (misplaced)} \\
0, & \text{if } a_i \in b_i \text{ (correctly placed)}
\end{cases}
$$

Effectively calculating the Hamming-Distance and assigning it to the nodes serves as a helpful means delineating whether it would be in our best interest to expand the frontier utilizing that node . This will serve as our heuristic 

# 3. State Space Representation 

The **State Space** is represented utilizing two lists . **Large disks** are represented by a circular list where each element corresponds to the number stamped on a large disk and a set of **Smaller disks** placed on top of corresponding larger disks which include a disk whose value is `0` , this corresponds to an empty position which determines our step size.

# 4. State Transition 

The **State Transition** is contingent on the step size which is determined by the $i$-th value in the **Large Disks** list ( where $i$ corresponds to the index of the `0` value in the **Small Disks** list ) . This step value , which we shall denote `k` , allows us to swap given 4 different options . 
- Swap `k` left
- Swap `k` right 
- Swap 1 left
- Swap 1 right
# 5. Programming Language

We have chosen to implement the Solution for the AB Berlin Puzzle sort utilizing the Python Programming Language for its simplicity and wide variety of pre-existing libraries . 