Imagine your a cashier and your trying to give people change while giving them the least amount of coins possible . Using a table we log the best way to create `n` amount using `m` change . and in doing so we can find work up the subproblems stored inside the table to find the optimal means of finding `n` amount .  

```c
F[0] <- 0 
for i <- 1 to n do 
	temp <- ∞  , j <- 1 
	while j <= m and i >= D[j] do 
		temp <- min(F[i - D[j]] , temp)
		j <- j + 1 
	F[i] <- temp + 1 
return F[n] 
``` 
 ___
 Tags : #programming #algorithms 