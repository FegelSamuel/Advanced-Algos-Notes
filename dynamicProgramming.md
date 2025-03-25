# Dynamic Programming
  * Dynamic Programming, or DP, is the method of sovling a problem using subsolutions. Recall that divide and conquer uses subproblems.
  * `f(n) = g( f(1), f(2), f(3), ..., f(n - 1))`
## Fibonacci Series
### Naiive Approach
```C
fib(int n) {
  if (n <= 1) return n;
  return fib(n - 1) + fib(n - 2);
}
```

### DP Approach
n is your input. You can get away with only having three spaces in your array, giving you an O(1) space.
```C
f[0] = 0, f[1] = 1,
for (i = 2 - n) 
  f[i] <- f[i - 1] + f[i - 2]
```
See me for an explanation if you want more. 

