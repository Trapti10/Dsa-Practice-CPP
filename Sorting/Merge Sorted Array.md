# 🔗 🔀 Problem: Merge Sorted Array

You can read the problem description here : [Problem](https://leetcode.com/problems/merge-sorted-array/)

##  Problem Statement
You are given two integer arrays `nums1` and `nums2`, both sorted in non-decreasing order, along with two integers `m` and `n` representing how many elements from each array should be considered.

Your task is to **merge nums2 into nums1** so that `nums1` becomes one sorted array.  
`nums1` has a size of `m + n`, where the last `n` values are zeros and should be ignored during merging.

The merged result must be stored **inside nums1**.

---

## 💻 Example

**Example 1:**  
**Input:**  
`nums1 = [1,2,3,0,0,0], m = 3`  
`nums2 = [2,5,6], n = 3`  
**Output:** `[1,2,2,3,5,6]`

**Example 2:**  
**Input:**  
`nums1 = [1], m = 1`  
`nums2 = [], n = 0`  
**Output:** `[1]`

**Example 3:**  
**Input:**  
`nums1 = [0], m = 0`  
`nums2 = [1], n = 1`  
**Output:** `[1]`

---

## 🧠 My Approach
I used a **three-pointer technique** starting from the **end** of the arrays:

- Set `i = m - 1` for nums1  
- Set `j = n - 1` for nums2  
- Set `k = m + n - 1` for placing elements in nums1  

Why from the end?  
Because nums1 has empty space at the back, so filling from the back avoids overwriting valid values.

Steps:
- Compare `nums1[i]` and `nums2[j]`, place the larger at `nums1[k]`.
- Move the pointer (`i` or `j`) and also `k`.
- If nums2 still has elements left, fill them into nums1.

---

🕒 Time Complexity :

Each element is processed once → O(m + n)

💾 Space Complexity :

No extra array used → O(1)

---

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int i = m - 1;
        int j = n - 1;
        int k = m + n - 1;

        while (i >= 0 && j >= 0) {
            if (nums1[i] > nums2[j]) {
                nums1[k--] = nums1[i--];
            } else {
                nums1[k--] = nums2[j--];
            }
        }

        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
};
