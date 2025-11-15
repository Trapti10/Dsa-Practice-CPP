# 🔗🔄 Problem: Reverse String

You can read the problem description here : [Problem](https://leetcode.com/problems/reverse-string/)

## Problem Statement
Write a function that reverses a string.  
The input string is given as an array of characters `s`.  

You must do this by modifying the input array **in-place** with **O(1)** extra memory.

---

## 💻 Example

**Example 1:**  
**Input:** `s = ["h","e","l","l","o"]`  
**Output:** `["o","l","l","e","h"]`

**Example 2:**  
**Input:** `s = ["H","a","n","n","a","h"]`  
**Output:** `["h","a","n","n","a","H"]`

---

## 🧠 My Approach
I used the **two-pointer technique** to reverse the string **in-place**.

- Initialize two pointers:  
  - `f` (front) → start of the array  
  - `e` (end) → end of the array  
- Swap `s[f]` and `s[e]`.  
- Move both pointers towards the center (`f++`, `e--`).  
- Continue until `f <= e`.  

This approach efficiently reverses the array without using any extra space.

---

🕒 Time Complexity :

We visit each element once and swap → O(n)

💾 Space Complexity :

Only a few variables used → O(1)

---

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    void reverseString(vector<char>& s) {
        int f = 0, e = s.size() - 1;
        while (f <= e) {
            swap(s[f], s[e]);
            f++;
            e--;
        }
    }
};
