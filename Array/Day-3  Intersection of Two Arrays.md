# 🔗 Problem: Intersection of Two Arrays  

**You can read the problem description here: [Problem Link](https://leetcode.com/problems/intersection-of-two-arrays/description/)**  

## 📄 Problem Statement  
Given two integer arrays `nums1` and `nums2`, return an array of their intersection.  
Each element in the result must be **unique**, and you may return the result in **any order**.

---

## 💻 Example  

**Example 1:**  
**Input:** `nums1 = [1,2,2,1], nums2 = [2,2]`  
**Output:** `[2]`  

**Example 2:**  
**Input:** `nums1 = [4,9,5], nums2 = [9,4,9,8,4]`  
**Output:** `[9,4]`  
**Explanation:** `[4,9]` is also accepted.

---

## 🧠 My Approach  
First, I stored all elements of `nums1` inside an unordered set so that duplicates are automatically removed and lookups become faster.  
Then, I looped through each element of `nums2` and checked if it exists in the set.  
If yes, I inserted it into another set `result` — this way, only unique elements are added.  
Finally, I converted the set `result` into a vector and returned it.  

---

🕒 Time Complexity

Building the first set → O(n)

Checking intersection → O(m)
✅ Overall: O(n + m)

💾 Space Complexity

Using two sets → O(n + m)

---

## ⚙️ Solution Code  
##Code (C++)  
```cpp
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
         unordered_set<int> s(nums1.begin(), nums1.end());
         unordered_set<int> result;

         for (int num : nums2) {
             if (s.count(num)) {
                 result.insert(num);
             }
         }

         return vector<int>(result.begin(), result.end());
    }
};
