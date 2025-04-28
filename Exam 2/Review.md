# Samuel Ma's Exam 2 Review
## Dynamic Programming
I think this is important to mention that dynamic programming is similar to divide and conquer, yet the difference is that you are building on subsolutions instead of building on subproblems.
### Fibonacci Sequence
So here is a naive way to do the nth number in the fibonacci series.
```C
int fib(int n) {
  if (n <= 1) {
    return n;
  }
  return fib(n - 1) + fib(n - 2);
}
```
The time complexity for this is O(2^n). Pretty bad lol. Inputs of just about 50 will make you see that it takes a long time. Inputs of like, 100 might not even run properly. How can we improve this?
#### Recurrence Relation (naive)
```bash
T(n) = T(n - 1) + T(n - 2) + O(1)  # Function calls and O(1) base case
```
#### Recurrence Tree
![visualization](https://github.com/user-attachments/assets/a70df09e-096f-4297-b4b2-139b676b6223)
#### Dynamic Programming Implementation 1 (Top-Down)
The idea is similar to the recursive idea. We can get away with having an auxiliary data structure to hold numbers we've already seen. For example, a hashmap can work, but I'm too lazy to code it, so we're going to use an array and something that checks "hey does this exist" before going into a recursive call. 
```C
int fibonacci(int n, int memo[]) { 
    // the int array should be of size n + 1 and all of its members should start at -1
  if (n <= 1) {
    return n;
  }
  if (memo[n] != -1) { 
  // here, if we've already seen the number before, we realize that we can just get away with returning that number. 
    return memo[n];
  }
  memo[n] = fibonacci(n - 1, memo) + fibonacci(n - 2, memo);
  return memo[n]; // notice we return memo of (10) if n = 10
}

```
This idea is memorization. Important concept! We cut down the chaff and just remember subsolutions to the problem. We are building on the subsolutions of previous fib calls. 
#### New Recurrence Tree
![visualization](https://www.baeldung.com/wp-content/uploads/sites/4/2020/06/Fibonacci-memoization.svg)
Now our algorithm runs in O(n). 
#### Dynamic Programming Implementation 2 (Bottom-Up)
First, we have f(0) and f(1) by default. Then we calculate f(2) by adding f(1) and f(0). Then we calculate f(2) by adding f(1) and f(2). So on and so forth until f(n) is calculated with f(n - 1) and f(n - 2).
```C
algorithm BottomUpFibonacci(N):
    // INPUT
    //   N = a non-negative integer
    // OUTPUT
    //   The N-th Fibonacci number

    if N = 0 or N = 1:
        return N

    A <- 0
    B <- 1

    for I <- 2 to N:
        Temp <- A + B
        A <- B
        B <- Temp

    return B
```
This one is also O(n) but the n here is nonnegligibly smaller than the above implementation due to recursion call stacks having a lot of overhead. This implementation is considered better, at least by Badhrachalam Chitturi.
### MSS (Maximum Subarray Sum)
This one is pretty difficult for me (like most advanced algos lol), so shoot me an email or text me if you need help with this. 


