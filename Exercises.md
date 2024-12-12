> [!example] 
> Write pseudocode of the greedy algorithm for the change-making problem, with an amount n and coin denominations d1 > d2 > ... > dm as its input. What is the time efficiency class of your algorithm? 

```c
function makeChange(n, denominations):
    Input: n (total amount), denominations (array of coin values in descending order: d1 > d2 > ... > dm)
    Output: A list of the number of coins for each denomination

    result = []  // Initialize an empty list to store the number of coins for each denomination
    for coin in denominations:
        count = n // coin  // Determine the maximum number of coins of this denomination
        result.append(count)  // Add this count to the result
        n = n % coin  // Update the remaining amount

    if n > 0:  // If there's a remainder, the greedy method may not work
        return "No solution with given denominations"
    else:
        return result

```