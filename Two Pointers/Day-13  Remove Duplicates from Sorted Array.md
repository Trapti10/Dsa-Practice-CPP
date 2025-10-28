# 🔗 🧹 Problem: Remove Duplicates from Sorted Array

You can read the problem description here:  [Problem](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

## Problem Statement
Given an integer array `nums` sorted in non-decreasing order, **remove the duplicates in-place** such that each unique element appears only once.  
The relative order of the elements should be kept the same.

Return the **number of unique elements** `k`.  
The first `k` elements of `nums` should contain the unique numbers in sorted order. The remaining elements beyond index `k - 1` can be ignored.

---

## 💻 Example

**Example 1:**  
**Input:** `nums = [1,1,2]`  
**Output:** `2, nums = [1,2,_]`  

**Example 2:**  
**Input:** `nums = [0,0,1,1,1,2,2,3,3,4]`  
**Output:** `5, nums = [0,1,2,3,4,_,_,_,_,_]`  

---

## 🧠 My Approach

I used the **two-pointer technique** to remove duplicates in-place:

- Use a pointer `j` to mark the position of the next unique element.  
- Iterate with `i` through the array starting from index `1`.  
- If `nums[i] != nums[j-1]`, it is a new unique element → assign it to `nums[j]` and increment `j`.  
- At the end, `j` represents the number of unique elements `k`.

---

🕒 Time Complexity

Single pass through the array → O(n)

💾 Space Complexity

In-place, no extra array used → O(1)

## ⚙️ Code (C++)

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int n = nums.size();
        int j = 1;
        for(int i = 1; i < n; i++){
            if(nums[i] != nums[j-1]){
                nums[j] = nums[i];
                j++;
            }
        }
        return j;
    }
};
