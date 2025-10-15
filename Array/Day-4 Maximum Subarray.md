🧩 🔗  Problem: Maximum Subarray

**You can read the problem description  here : [Problem Link](https://leetcode.com/problems/maximum-subarray/)**

## 📄 Problem Statement
Given an integer array `nums`, find the **subarray with the largest sum** and return its sum.

---

## 💻 Example

**Example 1:**  
**Input:** `nums = [-2,1,-3,4,-1,2,1,-5,4]`  
**Output:** `6`  
**Explanation:** The subarray `[4,-1,2,1]` has the largest sum 6.

**Example 2:**  
**Input:** `nums = [1]`  
**Output:** `1`  
**Explanation:** The subarray `[1]` has the largest sum 1.

**Example 3:**  
**Input:** `nums = [5,4,-1,7,8]`  
**Output:** `23`  
**Explanation:** The subarray `[5,4,-1,7,8]` has the largest sum 23.

---

## 🧠 My Approach
I used **Kadane's Algorithm** here.  
- I keep a variable `currentSum` to track the sum of the subarray ending at the current index.  
- If `currentSum` becomes negative, I reset it to 0 because a negative sum will reduce the total sum of any future subarray.  
- I also keep `maxSum` to store the maximum sum found so far while iterating.  
- At the end, `maxSum` contains the sum of the subarray with the largest sum.

---

🕒 Time Complexity
We traverse the array once → O(n), where n is the size of nums.

💾 Space Complexity
Only a few extra variables are used → O(1).

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int maxSum = nums[0];
        int currentSum = 0;
        
        for(int num : nums) {
            currentSum += num;
            if(currentSum > maxSum) maxSum = currentSum;
            if(currentSum < 0) currentSum = 0;
        }
        
        return maxSum;
    }
};

