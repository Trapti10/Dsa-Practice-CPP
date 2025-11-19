# 🔗🌟 Problem: Maximum Average Subarray I

You can read the problem description here : [Problem](https://leetcode.com/problems/maximum-average-subarray-i/)

## Problem Statement
You are given an integer array `nums` consisting of `n` elements, and an integer `k`.

Find a **contiguous subarray** whose length is equal to `k` that has the **maximum average value**, and return this value.

Any answer with a calculation error less than `10^-5` will be accepted.

---

## 💻 Example

**Example 1:**  
**Input:** `nums = [1,12,-5,-6,50,3], k = 4`  
**Output:** `12.75000`  
**Explanation:**  
Maximum average is `(12 - 5 - 6 + 50) / 4 = 51 / 4 = 12.75`

**Example 2:**  
**Input:** `nums = [5], k = 1`  
**Output:** `5.00000`

---

## 🧠 My Approach

This is a classic **Sliding Window** problem.

- First, calculate the sum of the **first `k` elements`** → This becomes your initial window sum.  
- Then slide the window by **1 step each time**:  
  - Add the new element → `nums[i]`  
  - Remove the outgoing element → `nums[i - k]`  
- Keep updating the **maximum window sum**.  
- Finally, return `maxSum / k` to get the maximum average.

This avoids recalculating sums every time and keeps the solution efficient.

---

🕒 Time Complexity:

Sliding window updates each element exactly once → O(n)

💾 Space Complexity:

No extra data structures used → O(1)

---

## ⚙️ Code (C++)

```cpp
class Solution {
public:
    double findMaxAverage(vector<int>& nums, int k) {
        double windowSum = 0;
          
        for(int i = 0; i < k; i++){
            windowSum += nums[i];
        }

        double maxSum = windowSum;

        for(int i = k; i < nums.size(); i++){
            windowSum += nums[i] - nums[i - k];
            maxSum = max(maxSum, windowSum);
        } 

        return maxSum / k;
    }
};
