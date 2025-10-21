# 🔗🧩 Problem: Intersection of Multiple Arrays

You can read the problem description here: [Problem](https://leetcode.com/problems/intersection-of-multiple-arrays/).

##  Problem Statement
Given a 2D integer array `nums` where `nums[i]` is a non-empty array of distinct positive integers,  
return the list of integers that are present in **each array** of `nums`, sorted in ascending order.

---

## 💻 Example

**Example 1:**  
**Input:** `nums = [[3,1,2,4,5],[1,2,3,4],[3,4,5,6]]`  
**Output:** `[3,4]`  
**Explanation:** The integers `3` and `4` are present in all arrays.

**Example 2:**  
**Input:** `nums = [[1,2,3],[4,5,6]]`  
**Output:** `[]`  
**Explanation:** No integer is common in both arrays, so the result is empty.

---

## 🧠 My Approach
- I first took the first array and stored its elements in a set.  
- Then for every next array, I compared its elements with the previous set to keep only the common elements.  
- I used another set to store the intersection for each step and replaced the old one.  
- After all iterations, the remaining elements in the set are the ones common to all arrays.  
- Finally, I converted the set into a vector and sorted it in ascending order before returning.

---

🕒 Time Complexity

Let n be the number of arrays and m be the average number of elements in each array.

Each intersection step takes approximately O(m).

Hence, the total time complexity is O(n * m).

💾 Space Complexity

We use extra sets to store intermediate intersections → O(m).


## ⚙️ Code (C++)
```cpp
class Solution {
public:
    vector<int> intersection(vector<vector<int>>& nums) {
        unordered_set<int> arr1(nums[0].begin(), nums[0].end());
        
        for (int i = 1; i < nums.size(); i++) {
            unordered_set<int> arr2(nums[i].begin(), nums[i].end());
            unordered_set<int> arr;
            
            for (int num : arr1) {
                if (arr2.count(num)) {
                    arr.insert(num);
                }
            }
            arr1 = move(arr);
        }

        vector<int> result(arr1.begin(), arr1.end());
        sort(result.begin(), result.end());

        return result;
    }
};

