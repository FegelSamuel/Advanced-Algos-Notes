# Greedy Algorithms
Greedy algorithms are algorithms that always pick the most locally optimal solution in the hope that it's optimal. A big thing to note about greedy algorithms is that they may not be optimal. 

<br>

An example of a greedy algorithm is something like Fractional Knapsack or Activity Selection Problem. 

## Defining a greedy algorithm
### Define your optimization criteria
Decide what "best" means in the context of your problem (such as smallest cost, largest value, best ratio. In the context of Fractional Knapsack, we select the biggest ratio between value and weight) 
### Make the locally optimal choice
At each step, pick the best looking choice without considering any previous iterations (in Fractional Knapsack, we sort the array based off of deriving the relationship between weight and value, then select until we exceed max weight)
