# Greedy Algorithms
Greedy algorithms are algorithms that always pick the most locally optimal solution in the hope that it's optimal. A big thing to note about greedy algorithms is that they may not be optimal. 

<br>

An example of a greedy algorithm is something like Fractional Knapsack or Activity Selection Problem. 

## Defining a greedy algorithm
### Define your optimization criteria
Decide what "best" means in the context of your problem (such as smallest cost, largest value, best ratio. In the context of Fractional Knapsack, we select the biggest ratio between value and weight) 
### Make the locally optimal choice
At each step, pick the best looking choice without considering any previous iterations (in Fractional Knapsack, we sort the array based off of deriving the relationship between weight and value, then select until we exceed max weight)
### Proving that a greedy algorithm is optimal
You can use a greedy approach for any problem. Proving that something is greedy at all is trivial. However, proving that a greedy algorithm is OPTIMAL is much less straightforward. Proving an approach is optimal isn't standardized at all. The most consistent thing you can use for proving a greedy algorithm is optimal is usually **proof by contradiction**. 
#### Proof by Contradiction Review
To prove something to be true, you can disprove its negation. For example, if I want to prove that F is true, I would assume !F to be true. Then I provide just one case where !F fails. Therefore, !(!F) <-> F

<br>

Another example is: Prove that iff n^2 is even, n is even where n is any number in the set of all integers.

First, assume n^2 is even and n is odd, which would make the implication above not work (or that n^2 is odd and n is even, both should be used because it's an iff). Then we provide a case that makes the assumption false. For example, let n^2 be 4. 4 is even. n is 2. 2 is even. n^2 being even -> n being odd gives us a false. To prove the other half of the double implication, we can n^2 be 9. 9 is odd. n is 3. 3 is odd. n^2 being odd -> n being even gives us a false. We've disproven the negation of what we want to prove, therefore, n^2 being even doubly implies that n is even. 

### Proving Fractional Knapsack
We are given an array of gold bars (A). Each gold bar (g) has a value (v) and a weight (w). We are given a maximum weight that we can hold (M). We want the maximum value of gold bars without going over our maximum weight. We can take parts of gold bars (not 0/1 knapsack problem). The approach is to sort A (this will take O(nlog(n)) time where n is the length of A) by descending value/weight ratios. We then add our values V and weights W until we hit our maximum weight (M). This subroutine runs in O(n) time. The entire algorithm is O(nlogn) time. 

<br>

Straightforward algorithm, right? Let's prove it's optimal. 

<br>

#### Claim: 
The greedy solution is optimal
#### Solution
We want the maximum value of gold bars without going over our maximum weight. We define density as d = v / w. Let G be our greedy solution and O be any optimal solution. The first gold bar picked by G we can call f. If O has f, G is consistent with O so far. If O does NOT have f, we may replace any gold bar in O with f because f has a higher d. O will eventually be transformed into G or give an equivalent solution (ties are harmless). 


