### **1. Introduction to Algorithms and Asymptotic Analysis**
- **Definition of an Algorithm:** A solution to a problem that has an end (NO INFINITE LOOPS).
- **Benchmarking Issues:** Time Complexity (space is whatever)

---

### **2. Mathematical Foundations**
- **Logs:**
  
  ![Base Log Properties](https://github.com/user-attachments/assets/c8674c86-5d4c-461f-a44f-0b849c5337f8)
  
  ![Change of Base](https://github.com/user-attachments/assets/8f1a53b5-bee4-40f5-b6f3-1bb0418ae9fb)
  
  ![Special](https://github.com/user-attachments/assets/51a67818-67ed-4c26-891f-7d8e321880d2)
  
  ![(n == small)->(log(n + 1) ~= n)](https://github.com/user-attachments/assets/0889078a-65d2-40b1-85c6-10184507bc7f)
  
- **Proof Techniques:**
   #### Direct Proof
   ![Direct Proof definition](https://github.com/user-attachments/assets/75e44e63-cfc3-4ff1-b425-7dbb2861abcd)
  
  **Here's an exercise, prove that if n is an even integer, n^2 is even as well.**
   #### Contradiction
   Negate what you're trying to prove, then show an instance where that statement is false.
   #### Induction
   Base Step -> Inductive Step (I'm gatekeeping this lol)

---

### **Asymptotic Notations and Their Definitions**  

Asymptotic notations describe the growth rate of functions, mainly used in algorithm analysis to classify time complexity. Below are the five major asymptotic notations:

---

## **1. Big-O Notation (O)**
### **Definition:**  
Big-O notation represents the **upper bound** of a function's growth rate. It provides an upper limit on how an algorithm behaves in the worst case.  

**Formal Definition:**  
A function `f(n) = O(g(n))` if there exist positive constants `c` and `d` such that:  
`f(n) ≤ c * g(n)` for all `n ≥ d`.  

👉 **"At most" growth rate.**  

**Example:**  
Let `f(n) = 3n² + 5n + 7`.  
Since `3n² + 5n + 7 ≤ 4n²` for large `n`, we can write:  
`f(n) = O(n²)`.  
Here, `g(n) = n²`, and we can choose `c = 4` and `d = 1`.

---

## **2. Big-Theta Notation (Θ)**
### **Definition:**  
Big-Theta notation provides a **tight bound** on the growth rate of a function. It means that the function grows at the same rate, both upper and lower bounded by another function.  

**Formal Definition:**  
A function `f(n) = Θ(g(n))` if there exist positive constants `c1`, `c2`, and `d` such that:  
`c1 * g(n) ≤ f(n) ≤ c2 * g(n)` for all `n ≥ d`.  

👉 **"Exact" growth rate.**  

**Example:**  
Let `f(n) = 5n + 3`.  
For large `n`, we can find constants such that:  
`2n ≤ 5n + 3 ≤ 6n` for all `n ≥ 1`.  
Thus, `f(n) = Θ(n)`.

---

## **3. Big-Omega Notation (Ω)**
### **Definition:**  
Big-Omega notation provides a **lower bound** on a function's growth rate. It describes the best-case or at least how fast a function will grow.  

**Formal Definition:**  
A function `f(n) = Ω(g(n))` if there exist positive constants `c` and `d` such that:  
`f(n) ≥ c * g(n)` for all `n ≥ d`.  

👉 **"At least" growth rate.**  

**Example:**  
Let `f(n) = 4n² + 10n + 6`.  
Since `4n² + 10n + 6 ≥ n²` for large `n`, we can write:  
`f(n) = Ω(n²)`.  
Here, we can choose `c = 1` and `d = 1`.

---

## **4. Little-o Notation (o)**
### **Definition:**  
Little-o notation represents a **strict upper bound**, meaning the function grows **strictly slower** than another function.  

**Formal Definition:**  
A function `f(n) = o(g(n))` if for all positive constants `c`, there exists `d` such that:  
`f(n) < c * g(n)` for all `n ≥ d`.  

👉 **"Grows strictly slower than"** `g(n)`.  

**Example:**  
Let `f(n) = n` and `g(n) = n²`.  
Since `n` grows **strictly slower** than `n²`, we write:  
`f(n) = o(n²)`.  
This means that no matter how large we multiply `g(n)`, `f(n)` will always grow slower.

---

## **5. Little-Omega Notation (ω)**
### **Definition:**  
Little-Omega notation represents a **strict lower bound**, meaning the function grows **strictly faster** than another function.  

**Formal Definition:**  
A function `f(n) = ω(g(n))` if for all positive constants `c`, there exists `d` such that:  
`f(n) > c * g(n)` for all `n ≥ d`.  

👉 **"Grows strictly faster than"** `g(n)`.  

**Example:**  
Let `f(n) = n²` and `g(n) = n`.  
Since `n²` grows **strictly faster** than `n`, we write:  
`f(n) = ω(n)`.

---

## **Summary Table**
| Notation  | Meaning | Example |
|-----------|------------------------------|----------------------|
| **Big-O (O)** | Upper bound (worst-case) | `f(n) = O(n²)` |
| **Big-Theta (Θ)** | Tight bound (exact growth rate) | `f(n) = Θ(n²)` |
| **Big-Omega (Ω)** | Lower bound (best-case) | `f(n) = Ω(n²)` |
| **Little-o (o)** | Strictly slower than | `f(n) = o(n²)` |
| **Little-omega (ω)** | Strictly faster than | `f(n) = ω(n)` |

---

### **5. Function Comparison and Recurrence Relations**
- **Types of Function Growth:** 
 - Polynomially greater than or less than a certain function involves the bottom row\
   
   | **Growth Type**      | **Example Function**      | **Growth Rate**               |
   |----------------------|--------------------------|------------------------------|
   | **Functional Growth** | `f(n) = 3n² + 5n + 7`    | General function behavior    |
   | **Asymptotic Growth** | `f(n) = O(n²)`          | Focuses on dominant term    |
   | **Polynomial Growth** | `f(n) = 2n³ + 4n²`      | Has the form `n^k`          |
   
  - **Function Hierarchy:** Identifying the fastest-growing terms.\
 #### Logarithms
 log(n)
 #### Polynomial
 n, n^2, so on so forth
 #### Exponential 
 2^n
 
---

### **6. Solving Recurrences**
- **Iteration Method:** Expanding recurrence relations step by step. Only works when you're comparing polynomially greater than, less than, or polynomially equivalent functions. 
- **Recursion Tree Method:** Breaking down recurrences visually.

---

### **7. Advanced Asymptotic Techniques**
- **Master Theorem:** A powerful tool for solving divide-and-conquer recurrences. Plug and play moment.
   ### **Master Theorem**  
The **Master Theorem** is used to analyze the time complexity of divide-and-conquer recurrences of the form:  

**T(n) = aT(n/b) + f(n)**  

Where:  
- `T(n)` = total time complexity  
- `a` = number of recursive subproblems  
- `b` = factor by which the problem size is reduced  
- `f(n)` = additional work done outside recursion (e.g., merging, dividing)  

---

### **Three Cases of the Master Theorem**  

| Case | Condition | Complexity |
|------|-----------|------------|
| **Case 1** | If `f(n) = O(n^c)` where `c < log_b(a)` | `T(n) = Θ(n^(log_b(a)))` |
| **Case 2** | If `f(n) = Θ(n^c)` where `c = log_b(a)` | `T(n) = Θ(n^c log n)` |
| **Case 3** | If `f(n) = Ω(n^c)` where `c > log_b(a)`, and `a*f(n/b) ≤ k*f(n)` for some `k < 1` | `T(n) = Θ(f(n))` |

---

### **Examples**  

#### **Example 1: Merge Sort**
Given:  
`T(n) = 2T(n/2) + O(n)`  
- `a = 2`, `b = 2`, `f(n) = O(n)`  
- `log_2(2) = 1` and `f(n) = O(n^1)`  
- Case 2 applies → **T(n) = Θ(n log n)**  

#### **Example 2: Binary Search**
Given:  
`T(n) = T(n/2) + O(1)`  
- `a = 1`, `b = 2`, `f(n) = O(1)`  
- `log_2(1) = 0` and `f(n) = O(n^0)`  
- Case 1 applies → **T(n) = Θ(log n)**  

---

### **8. Sorting Algorithms**
Look up Bubble Sort (swap adjacents), Insertion Sort (Partitions),  Selection Sort (run findMin or findMax a fuck ton of times), Merge Sort (it's merge sort), Heap Sort (Run heapify on the first n/2 elements of the array in a specific order), Quicksort (partitions).

---

### **9. Divide and Conquer Algorithms**

I'M GATEKEEPING THIS 

---

### **10. Advanced Algorithmic Techniques**
- **Maximum Subarray Sum (MSS):** 

 ### **MSS (Maximum Subarray Sum Problem)**  

The **Maximum Subarray Sum (MSS) problem** is a classic problem in computer science that involves finding the contiguous subarray within a given one-dimensional array that has the largest sum.  

---

### **Problem Definition**  
Given an array of integers:  
`arr = [−2, 1, −3, 4, −1, 2, 1, −5, 4]`  

The goal is to find a **contiguous subarray** that has the largest sum.  

#### **Example:**  
For the given array:  
- The subarray `[4, -1, 2, 1]` has the maximum sum of `6`.  

---

### **Approaches to Solve MSS**  

| Algorithm | Time Complexity | Explanation |
|-----------|----------------|-------------|
| **Brute Force** | O(n²) | Check all possible subarrays and find the maximum sum. |
| **Kadane’s Algorithm** | O(n) | Iteratively compute the maximum sum ending at each index. |
| **Divide and Conquer** | O(n log n) | Recursively divide the array and find the maximum sum across left, right, and cross-subarrays. |

---

### **Kadane’s Algorithm (Optimal Approach, O(n))**  

1. Initialize `max_sum = arr[0]` and `current_sum = arr[0]`.  
2. Iterate through the array:  
   - Update `current_sum = max(arr[i], current_sum + arr[i])`  
   - Update `max_sum = max(max_sum, current_sum)`  
3. Return `max_sum`  

#### **Kadane’s Algorithm Example**
For `arr = [-2, 1, -3, 4, -1, 2, 1, -5, 4]`:  

| Index | Element | Current Sum | Max Sum |
|--------|---------|------------|---------|
| 0      | -2      | -2         | -2      |
| 1      | 1       | 1          | 1       |
| 2      | -3      | -2         | 1       |
| 3      | 4       | 4          | 4       |
| 4      | -1      | 3          | 4       |
| 5      | 2       | 5          | 5       |
| 6      | 1       | 6          | 6       |
| 7      | -5      | 1          | 6       |
| 8      | 4       | 5          | 6       |

Final **maximum sum** = `6`.  

```C
int maxSubarraySum(vector<int> &arr) {
    int res = arr[0];
  
    // Outer loop for starting point of subarray
      for(int i = 0; i < arr.size(); i++) {
        int currSum = 0;
      
        // Inner loop for ending point of subarray
        for(int j = i; j < arr.size(); j++) {
            currSum = currSum + arr[j];
          
            // Update res if currSum is greater than res
            res = max(res, currSum);
        }
    }
    return res;
}
```

- **Karatsuba’s Multiplication Algorithm:** Fast multiplication using divide and conquer.
  

Karatsuba's algorithm is a fast multiplication method that breaks down the multiplication of two large numbers into smaller multiplications. It reduces the time complexity from the traditional O(n²) to maybe (?) O(n^1.585) or O(n^(log base 3 of 2)), which makes it more efficient for large numbers.

### Steps of Karatsuba's algorithm:

1. **Split the numbers**:  
   Suppose you're multiplying two numbers, `x` and `y`. Split each number into two parts. For example:
   - Let `x = a * 10^m + b`
   - Let `y = c * 10^m + d`

   Here, `a` and `c` are the most significant parts of the numbers, and `b` and `d` are the least significant parts.

2. **Three multiplications**:  
   Instead of performing the traditional four multiplications (`a * c`, `a * d`, `b * c`, and `b * d`), Karatsuba calculates only three multiplications:
   - `p1 = a * c`
   - `p2 = b * d`
   - `p3 = (a + b) * (c + d)`

3. **Final result**:  
   Using the three results from the previous step, the final result is calculated as:
   - `result = p1 * 10^(2m) + (p3 - p1 - p2) * 10^m + p2`

This algorithm effectively reduces the number of multiplications needed, which is especially useful when multiplying very large numbers.
---
