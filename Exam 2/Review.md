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

<br>

The problem is:

> Given an array of integers (positive, negative, or zero), find the contiguous subarray (containing at least one number) which has the largest sum.

This is a classic **Dynamic Programming** problem and often taught via **Kadane’s Algorithm**.

### Dynamic Programming Idea:

- We define `maxEndingHere[i]` as the maximum sum of a subarray ending at position `i`.
- Recurrence relation:
  ```
  maxEndingHere[i] = max(arr[i], maxEndingHere[i-1] + arr[i])
  ```
- The idea is: at each step, either you start a new subarray at `i`, or you extend the previous subarray.

- The final answer is the maximum of all `maxEndingHere[i]`.

---

### C Implementation:

```c
#include <stdio.h>

int maxSubArraySum(int arr[], int n) {
    int maxSoFar = arr[0];
    int maxEndingHere = arr[0];

    for (int i = 1; i < n; i++) {
        // Extend or start a new subarray
        if (maxEndingHere + arr[i] > arr[i])
            maxEndingHere = maxEndingHere + arr[i];
        else
            maxEndingHere = arr[i];

        // Update max so far if needed
        if (maxEndingHere > maxSoFar)
            maxSoFar = maxEndingHere;
    }

    return maxSoFar;
}

int main() {
    int arr[] = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
    int n = sizeof(arr) / sizeof(arr[0]);

    int maxSum = maxSubArraySum(arr, n);
    printf("Maximum Subarray Sum is %d\n", maxSum);

    return 0;
}
```
(You would get `6` from this because the subarray `[4, -1, 2, 1]` has the maximum sum of `6`)

### Longest Common Substring and Subsequence
I think this one is a little less intuitive because it runs in a O(n * m) where n is string 1 length and m is string 2 length. Usually, dp would give us an O(n) time complexity but we can't get much better than this. 
#### Longest Common Substring
Definition: Find the longest contiguous (i.e., continuous) substring that appears in both strings.

<br>


Dynamic Programming idea:
```bash
  Use a table dp[i][j] where dp[i][j] stores the length of the longest common substring ending at str1[i-1] and str2[j-1].
  If str1[i-1] == str2[j-1], then dp[i][j] = dp[i-1][j-1] + 1.
  Otherwise, dp[i][j] = 0.
```
```C
void longestCommonSubstring(char *str1, char *str2) {
    int n = strlen(str1);
    int m = strlen(str2);
    int dp[n+1][m+1];
    int maxLength = 0;
    int endIndex = 0; // end index in str1

    // Initialize dp table
    for (int i = 0; i <= n; i++) {
        for (int j = 0; j <= m; j++) {
            if (i == 0 || j == 0)
                dp[i][j] = 0;
            else if (str1[i-1] == str2[j-1]) {
                dp[i][j] = dp[i-1][j-1] + 1;
                if (dp[i][j] > maxLength) {
                    maxLength = dp[i][j];
                    endIndex = i;
                }
            } else
                dp[i][j] = 0;
        }
    }

    printf("Length of Longest Common Substring: %d\n", maxLength);
    printf("Longest Common Substring: ");
    for (int i = endIndex - maxLength; i < endIndex; i++) {
        printf("%c", str1[i]);
    }
    printf("\n");
}
```
You need a table of n * m size and you calculate the size of each common substring (contiguous sequence of characters) for each n and m.

#### Longest Common Subsequence
Longest Common Subsequence is the longest noncontiguous string of numbers common between two strings. What we mean here is that 'abc' and 'adc' have a longest common subsequence of 'ac'. 
```C
void longestCommonSubsequence(char *str1, char *str2) {
    int n = strlen(str1);
    int m = strlen(str2);
    int dp[n+1][m+1];

    // Fill dp table
    for (int i = 0; i <= n; i++) {
        for (int j = 0; j <= m; j++) {
            if (i == 0 || j == 0)
                dp[i][j] = 0;
            else if (str1[i-1] == str2[j-1])
                dp[i][j] = dp[i-1][j-1] + 1;
            else
                dp[i][j] = (dp[i-1][j] > dp[i][j-1]) ? dp[i-1][j] : dp[i][j-1];
        }
    }

    // Now reconstruct the sequence
    int index = dp[n][m];
    char lcs[index+1];
    lcs[index] = '\0'; // Null-terminate the string

    int i = n, j = m;
    while (i > 0 && j > 0) {
        if (str1[i-1] == str2[j-1]) {
            lcs[index-1] = str1[i-1];
            i--;
            j--;
            index--;
        } else if (dp[i-1][j] > dp[i][j-1])
            i--;
        else
            j--;
    }

    printf("Length of Longest Common Subsequence: %d\n", dp[n][m]);
    printf("Longest Common Subsequence: %s\n", lcs);
}
```

