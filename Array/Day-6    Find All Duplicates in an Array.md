# 🔗🧩 Find All Duplicates in an Array

You can read the problem description here: [Problem](https://leetcode.com/problems/find-all-duplicates-in-an-array/description/).


## 📄 Problem Statement
Given an integer array `nums` of length `n` where all the integers of `nums` are in the range `[1, n]` and each integer appears at most twice, return an array of all the integers that appear twice.

You must write an algorithm that runs in **O(n)** time and uses only **constant auxiliary space**, excluding the space needed to store the output.

---

## 💻 Example

**Example 1:**  
**Input:** `nums = [4,3,2,7,8,2,3,1]`  
**Output:** `[2,3]`

**Example 2:**  
**Input:** `nums = [1,1,2]`  
**Output:** `[1]`

**Example 3:**  
**Input:** `nums = [1]`  
**Output:** `[]`

---

## 🧠 My Approach
I used an **unordered_set** to keep track of numbers that already appeared.  
- While iterating through the array, I check if the current number exists in the set.  
- If it does, it means it’s a duplicate, so I add it to the `duplicates` vector.  
- Otherwise, I insert the number into the set.  
- Finally, I return the vector containing all duplicate elements.

This approach ensures each element is checked only once, making it both clean and efficient.

---

🕒 Time Complexity - 

Each element is processed once → O(n)

Set operations (insert and lookup) take O(1) on average.

💾 Space Complexity - 

Extra space for unordered_set and duplicates list → O(n) in the worst case.

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        unordered_set<int>result;
        vector<int>duplicates;
        for(int num : nums){
            if(result.count(num)){
                duplicates.push_back(num);
            }
            else{
            result.insert(num);
            }
        }
        return duplicates;
    }
};
