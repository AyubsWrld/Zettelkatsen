When the **plan is constructed dynamically during execution**, useful when the environment is unknown or changes. Example: **LRTA*** (Learning Real-Time A*) updates its knowledge as it explores.

In this case the agent only knows list of allowed actions in state s , the step cost after s is known and a goal test . 

In **online search problems**, the goal is to reach the target with minimal cost while adapting to unknown environments, where performance is measured using the **competitive ratio** (comparing actual cost to the optimal cost if the search space were known), but the cost can be **infinite** if the agent reaches dead ends.

Hill-climbing is an Example of online search 

___
Tags : #ai #programming 