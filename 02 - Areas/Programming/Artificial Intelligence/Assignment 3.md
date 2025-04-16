1) **Which Network(s) can correctly represent P(Flavor,Wrapper,Shape)?** 
	- It can be represented by networks (ii) and (iii), but not by network (i). Since (ii) is fully coupled, any joint distribution can be represented utilizing this network. The generative process is reflected in (iii), where the machine chooses the taste, followed by a random selection of the form and wrapper, with the wrapper being decided by chance. (i) makes the mistaken assumption that shape and wrapping are independent.
2) **Which network is the best representation for this problem?**
	- Unlike (ii), (iii) is acyclic, making inference simpler. Its structure also matches the generative process, so probabilities are easier to elicit—and are already provided.
3) **Does network (1) assert that P(Wrapper|Shape)=PWrapper)?**
	- Because the wrapper and shape are d-separated the statement follows. 
4) **What is the probability that your candy has a red wrapper?**
	Derive flavor -> then we can decide the probability of the wrapper being red or brown. 


$$
P(\text{Red}) = \sum_f P(f) \cdot P(\text{Red} \mid f)
$$

$$
= 0.7 \times 0.8 + 0.3 \times 0.1
$$

$$
= 0.59
$$
5) **What is the probability that your candy is round?** 
	- For this we can derive whenever round is true. 
	- Since we know that 70% of candies are strawberry flavor, 30% are anchovy flavor
	- 80% of strawberry candies are round, 20% are square
	- 90% of anchovy candies are square, leaving the other 10% as round 
	- We are left with P(Shape=round) =  P(Shape=round|Flavor=strawberry) × P(Flavor=strawberry) + P(Shape=round|Flavor=anchovy) × P(Flavor=anchovy) so it follows from that we get : 0.8 × 0.7 + 0.1 × 0.3 = **0.59**
6) **In the box is a round candy with red wrapper. What is the probability that its flavor is strawberry?**
	- P(Flavor=strawberry | Shape=round, Wrapper=red)
	- P(Flavor=strawberry) × P(Shape=round | Flavor=strawberry) × P(Wrapper=red | Flavor=strawberry)
	- 0.7 × 0.8 × 0.8
	- which is equivalent to **0.448** 


## Question Two
___
Derive the remainders of each attribute 
the remainders for $A_1$, $A_2$, and $A_3$ respectively are as follows : 
- $R(A_1)$ : (4/5)(-2/4 log(2/4) - 2/4 log(2/4)) + (1/5)(-0 - 1/1 log(1/1)) = 0.800
- $R(A_2)$ : (3/5)(-2/3 log(2/3) - 1/3 log(1/3)) + (2/5)(-0 - 2/2 log(2/2)) ≈ 0.551
- R(A_3) : (2/5)(-1/2 log(1/2) - 1/2 log(1/2)) + (3/5)(-1/3 log(1/3) - 2/3 log(2/3)) ≈ 0.951

When we conduct our second split utilizing $A_2$ we get 
- $R(A_1)$ : (2/3)(-2/2 log(2/2) - 0) + (1/3)(-0 - 1/1 log(1/1)) = 0 
- R(A_3) :(1/3)(-1/1 log(1/1) - 0) + (2/3)(-1/2 log(1/2) - 1/2 log(1/2)) ≈ 0.667
given that we have arrived at a zero value ( minimum remainder value ), we can utilize it for the second split 

the final decision tree has the structure : 

- If A2 = 0, then Y = 0
- If A2 = 1 and A1 = 0, then Y = 0
- If A2 = 1 and A1 = 1, then Y = 1
