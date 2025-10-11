# Day 1 - Two Sum

## Two Sum Problem
You can view the problem description here: [Problem Link](https://leetcode.com/problems/two-sum/description/)

---

### 🧩 Problem Statement
Given an array of integers `nums` and an integer `target`, return the indices of the two numbers such that they add up to the target.

You may assume that each input will have exactly one solution, and you cannot use the same element twice.  
You can return the answer in any order.

---

### 📘 Examples

**Example 1:**  
Input: `nums = [2,7,11,15], target = 9`  
Output: `[0,1]`  
Explanation: Because `nums[0] + nums[1] == 9`, we return `[0, 1]`.

**Example 2:**  
Input: `nums = [3,2,4], target = 6`  
Output: `[1,2]`

**Example 3:**  
Input: `nums = [3,3], target = 6`  
Output: `[0,1]`

---

### ⚙️ Constraints
2 <= nums.length <= 10^4
-10^9 <= nums[i] <= 10^9
-10^9 <= target <= 10^9
Only one valid answer exists.



### 💭 My Approach
I used a simple **brute force** method to solve this problem.  
- I used two loops: the outer loop goes through each element, and the inner loop checks every next element.  
- For each pair, I checked if their sum equals the target.  
- If yes, I returned their indices immediately.  
- If no pair matched, I returned an empty vector.  

This approach is easy to understand and good for beginners, even though it’s not the most optimized one.

---

⏱️ Time & Space Complexity
🕒 Time Complexity
The code uses two nested loops → for each element, we check all other elements after it.
Therefore, Time Complexity = O(n²), where n is the size of the array.

💾 Space Complexity
We are only using a few extra variables (no additional data structures).
Hence, Space Complexity = O(1).

📝 Notes
This was my first DSA problem on LeetCode.

I understood how nested loops work for pair comparison.

Next, I’ll try to solve this with a better (optimized) approach using a hash map.

---

### 💻 Solution Code 

Code (C++)
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        for(int i = 0; i < nums.size(); i++) {
            for(int j = i + 1; j < nums.size(); j++) {
                if(nums[i] + nums[j] == target) {
                    return {i, j};
                }
            }
        }
        return {};
    }
};
