 It's likes climbing a hill while you still haven't reached the top . You look ahead and see that there is still a higher point so you traverse it , only stopping once you've reached the top . 

```c
function HILL-CLIMBING(problem) 

current <- MAKE-NODE(INITIAL-STATE[problem])
while(true) do 
 if VALUE[neighbor] <= VALUE[current] then 
	 return current  // peak found 
current <- neighbor 
```

- Stochastic Hill cl