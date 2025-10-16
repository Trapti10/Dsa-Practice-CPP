#  🔗 🧩 Problem: Contains Duplicate

You can read the problem description here : [Problem](https://leetcode.com/problems/contains-duplicate/description/).

## 📄 Problem Statement
Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct.

---

## 💻 Example

**Example 1:**  
**Input:** `nums = [1,2,3,1]`  
**Output:** `true`  
**Explanation:** The element `1` occurs at the indices `0` and `3`.

**Example 2:**  
**Input:** `nums = [1,2,3,4]`  
**Output:** `false`  
**Explanation:** All elements are distinct.

**Example 3:**  
**Input:** `nums = [1,1,1,3,3,4,3,2,4,2]`  
**Output:** `true`

---

## 🧠 My Approach
I used an **unordered_set** to keep track of numbers that have already appeared.  
- While iterating through the array, I check if the number already exists in the set.  
- If it does, it means there’s a duplicate, so I return `true`.  
- Otherwise, I insert the number into the set and continue.  
- If no duplicates are found by the end, I return `false`.

This approach helps quickly detect duplicates without sorting the array.

---

🕒 Time Complexity
Each lookup and insertion in an unordered_set is O(1) on average.

Hence, total complexity → O(n), where n is the size of nums.

💾 Space Complexity
Extra space used for the unordered_set → O(n) in the worst case.

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_set<int> result;
        for (int num : nums) {
            if (result.count(num))
                return true;
            result.insert(num);
        }
        return false;
    }
};
