# 🔗🧩 Problem: Binary Search

You can read the problem description here: [Problem](https://leetcode.com/problems/binary-search/).

## Problem Statement
Given an array of integers `nums` which is sorted in ascending order, and an integer `target`,  
write a function to search `target` in `nums`.  
If `target` exists, then return its index. Otherwise, return `-1`.

You must write an algorithm with **O(log n)** runtime complexity.

---

## 💻 Example

**Example 1:**  
**Input:** `nums = [-1,0,3,5,9,12], target = 9`  
**Output:** `4`  
**Explanation:** 9 exists in `nums` and its index is 4.

**Example 2:**  
**Input:** `nums = [-1,0,3,5,9,12], target = 2`  
**Output:** `-1`  
**Explanation:** 2 does not exist in `nums` so return -1.

---

## 🧠 My Approach
I applied the **Binary Search** algorithm since the array is sorted.  
- I used two pointers `s` (start) and `e` (end) to represent the current search range.  
- Calculated `mid` as the middle index.  
- If `nums[mid] == target`, we return `mid`.  
- If `nums[mid] < target`, I moved the start pointer to `mid + 1` because the target must be in the right half.  
- Otherwise, I moved the end pointer to `mid - 1`.  
- The loop continues until the target is found or the search range becomes invalid.

---

🕒 Time Complexity
The array is divided in half each iteration → O(log n).

💾 Space Complexity
Only a few integer variables are used → O(1).

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int s = 0, e = nums.size() - 1;
        int mid = s + (e - s) / 2;

        while (s <= e) {
            if (nums[mid] == target) {
                return mid;
            } 
            else if (nums[mid] < target) {
                s = mid + 1;
            } 
            else {
                e = mid - 1;
            }
            mid = s + (e - s) / 2;   
        }
        return -1;
    }
};
