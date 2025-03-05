Data structure design to handle very large amounts of a data . A B-tree can have multiple branches coming from the same node as opposed to just two present in a binary tree . B-trees are also self-balancing . They are like file cabinets with multiple levels of data . A key helps us find a specific node while segmented the layers of the tree into different levels . Sort of like how when we are looking for a book at the library we tend to sort the books out by categories or first letter which narrows our search . 

Each node within a B-tree has limited amount of children . 

### How searching works 
____
Starts at node -> if the key is greater go right , otherwise go left and if the key = node go in the middle . 

### How Insertion works
____
Start at root node -> navigate down the tree similar to how searching works . Insert where it fits and if overflow occurs , split the node and rebalance . 



___

Tags : #programming #algorithms 