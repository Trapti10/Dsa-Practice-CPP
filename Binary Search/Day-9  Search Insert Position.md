# 🔗🧩 Problem: Search Insert Position

You can read the problem description here: [Problem](https://leetcode.com/problems/search-insert-position/).

## Problem Statement
Given a sorted array of distinct integers and a `target` value, return the **index** if the target is found.  
If not, return the index where it would be if it were inserted in order.

You must write an algorithm with **O(log n)** runtime complexity.

---

## 💻 Example

**Example 1:**  
**Input:** `nums = [1,3,5,6], target = 5`  
**Output:** `2`

**Example 2:**  
**Input:** `nums = [1,3,5,6], target = 2`  
**Output:** `1`

**Example 3:**  
**Input:** `nums = [1,3,5,6], target = 7`  
**Output:** `4`

---

## 🧠 My Approach
I used **Binary Search** here as well:  
- Start with two pointers `s` and `e` for the start and end of the array.  
- Calculate `mid = s + (e - s)/2`.  
- If `nums[mid] == target`, return `mid`.  
- If `nums[mid] < target`, move the start pointer to `mid + 1`.  
- If `nums[mid] > target`, move the end pointer to `mid - 1`.  
- When the loop ends, `s` will be at the position where the target should be inserted.

---

🕒 Time Complexity:     

Binary search halves the array each iteration → O(log n)

💾 Space Complexity:      

Only a few variables used → O(1)

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int s = 0, e = nums.size() - 1;
        int mid  = s + (e - s)/2;
        
        while(s <= e){
            if(nums[mid] == target){
                return mid;
            }
            else if(nums[mid] < target){
                s = mid + 1;
            }
            else {
                e = mid - 1;    
            }
            mid = s + (e - s)/2;
        }
        return s;
    }
};
