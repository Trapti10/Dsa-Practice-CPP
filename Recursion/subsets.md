# 🧩 Problem: Subsets

You can read the problem description [here](https://leetcode.com/problems/subsets/).

## 📄 Problem Statement
Given an integer array `nums` of **unique elements**, return **all possible subsets** (power set).

The solution set must not contain duplicate subsets.  
You can return the subsets in any order.

---

## 💻 Examples

**Example 1:**  
**Input:** `nums = [1,2,3]`  
**Output:**  
`[[], [1], [2], [1,2], [3], [1,3], [2,3], [1,2,3]]`

**Example 2:**  
**Input:** `nums = [0]`  
**Output:** `[[], [0]]`

---

## 🧠 My Approach
I used **recursion (backtracking)** to generate all subsets.

- At each index, I have **two choices**:
  - Include the current element
  - Exclude the current element
- I move forward recursively until I reach the end of the array.
- When the index reaches the size of the array, I store the current subset in the answer.
- This way, all possible combinations are generated.

---

## ⚙️ Code (C++)
```cpp
class Solution {
private:
    void solve(vector<int>& nums, vector<int>& output, int index, vector<vector<int>>& ans) {
        if(index >= nums.size()) {
            ans.push_back(output);
            return;
        }

        // Exclude
        solve(nums, output, index + 1, ans);

        // Include
        output.push_back(nums[index]);
        solve(nums, output, index + 1, ans);
        output.pop_back();
    }

public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> ans;
        vector<int> output;
        solve(nums, output, 0, ans);
        return ans;
    }
};
