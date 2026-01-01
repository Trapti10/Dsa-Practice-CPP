# 🧩 Problem: Fibonacci Number

You can read the problem description here : [Problem](https://leetcode.com/problems/fibonacci-number/).

## 📄 Problem Statement
The Fibonacci sequence is defined as:
- F(0) = 0  
- F(1) = 1  
- F(n) = F(n - 1) + F(n - 2), for n > 1  

Given an integer `n`, return `F(n)`.

---

## 💻 Examples

**Example 1:**  
**Input:** `n = 2`  
**Output:** `1`  

**Example 2:**  
**Input:** `n = 3`  
**Output:** `2`  

**Example 3:**  
**Input:** `n = 4`  
**Output:** `3`  

---

## 🧠 My Approach
I used a **recursive approach** to solve this problem.

- If `n` is 0 or 1, I directly return the value because these are the base cases.
- For other values of `n`, I calculate the Fibonacci number by calling the function for `n-1` and `n-2`.
- The final answer is the sum of these two recursive calls.

This approach follows the Fibonacci definition directly.

---

🕒 Time Complexity :

Each call makes two recursive calls → O(2ⁿ)

💾 Space Complexity :

Recursive call stack can go up to n → O(n)

---

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    int fib(int n) {
        if(n == 0) return 0;
        if(n == 1) return 1;

        int ans = fib(n - 1) + fib(n - 2);
        return ans;
    }
};
