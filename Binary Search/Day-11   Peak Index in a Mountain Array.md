# 🔗 ⛰️ Problem: Peak Index in a Mountain Array

You can read the problem description here:  [Problem](https://leetcode.com/problems/peak-index-in-a-mountain-array/)

## 🔗 Problem Statement
You are given an integer mountain array `arr` of length `n` where the values **increase to a peak element and then decrease**.  

Return the **index of the peak element**.  

You must solve it in **O(log n)** time complexity.

---

## 💻 Example

**Example 1:**  
**Input:** `arr = [0,1,0]`  
**Output:** `1`  

**Example 2:**  
**Input:** `arr = [0,2,1,0]`  
**Output:** `1`  

**Example 3:**  
**Input:** `arr = [0,10,5,2]`  
**Output:** `1`  

---

## 🧠 My Approach

Since the array first increases and then decreases, the **peak element** is the point where `arr[mid] > arr[mid + 1]`.  
This pattern allows us to use **Binary Search** to find the peak efficiently.  

Steps:
1. Initialize `s = 0` and `e = arr.size() - 1`.  
2. Calculate `mid = s + (e - s) / 2`.  
3. If `arr[mid] < arr[mid + 1]`, it means we are on the **increasing** side → move right (`s = mid + 1`).  
4. Else, we are on the **decreasing** side → move left (`e = mid`).  
5. When `s == e`, both pointers will meet at the **peak index**.

---

🕒 Time Complexity :

Binary search divides the array in half each iteration → O(log n)

💾 Space Complexity :

Uses only a few variables → O(1).

## ⚙️ Code (C++)

```cpp
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& arr) {
        int s  = 0;
        int e = arr.size() - 1;
        int mid  = s + (e - s) / 2;
        while (s < e) {
            if (arr[mid] < arr[mid + 1]) {
                s = mid + 1; // move right
            } else {
                e = mid; // move left
            }
            mid = s + (e - s) / 2;
        }
        return s;
    }
};
