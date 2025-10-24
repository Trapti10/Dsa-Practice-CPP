# 🔗 🎯 Problem: Find First and Last Position of Element in Sorted Array

You can read the problem description here: [Problem](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/).

## Problem Statement
Given an array of integers `nums` sorted in non-decreasing order, find the **starting and ending position** of a given `target` value.  

If `target` is not found in the array, return `[-1, -1]`.  

You must write an algorithm with **O(log n)** runtime complexity.

---

## 💻 Example

**Example 1:**  
**Input:** `nums = [5,7,7,8,8,10], target = 8`  
**Output:** `[3,4]`  

**Example 2:**  
**Input:** `nums = [5,7,7,8,8,10], target = 6`  
**Output:** `[-1,-1]`  

**Example 3:**  
**Input:** `nums = [], target = 0`  
**Output:** `[-1,-1]`

---

## 🧠 My Approach

To achieve **O(log n)** runtime, I used **Binary Search** twice:  
1. **First Binary Search** → Find the first occurrence (leftmost index) of the target.  
2. **Second Binary Search** → Find the last occurrence (rightmost index) of the target.  

Steps:  
- Initialize `start = 0`, `end = nums.size() - 1`.  
- For **first position**: move `end` to `mid - 1` when you find the target (keep searching left).  
- For **last position**: move `start` to `mid + 1` when you find the target (keep searching right).  
- Return both indices as `[first, last]`.

---

🕒 Time Complexity:  
Each binary search runs in O(log n) → total O(log n).

💾 Space Complexity:  
Only a few extra variables used → O(1).

## ⚙️ Code (C++)

```cpp
class Solution {
public:
    int firstPosition(vector<int>& nums, int target) {
        int s = 0, e = nums.size() - 1;
        int ans = -1;
        while (s <= e) {
            int mid = s + (e - s) / 2;
            if (nums[mid] == target) {
                ans = mid;
                e = mid - 1;  // keep searching left
            } else if (nums[mid] < target) {
                s = mid + 1;
            } else {
                e = mid - 1;
            }
        }
        return ans;
    }

    int lastPosition(vector<int>& nums, int target) {
        int s = 0, e = nums.size() - 1;
        int ans = -1;
        while (s <= e) {
            int mid = s + (e - s) / 2;
            if (nums[mid] == target) {
                ans = mid;
                s = mid + 1;  // keep searching right
            } else if (nums[mid] < target) {
                s = mid + 1;
            } else {
                e = mid - 1;
            }
        }
        return ans;
    }

    vector<int> searchRange(vector<int>& nums, int target) {
        vector<int> ans(2, -1);
        ans[0] = firstPosition(nums, target);
        ans[1] = lastPosition(nums, target);
        return ans;
    }
};
