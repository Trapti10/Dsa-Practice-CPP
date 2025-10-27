#  🔗 🔢 Problem: Two Sum II - Input Array Is Sorted

You can read the problem description here: [Problem](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

## Problem Statement
Given a 1-indexed array of integers `numbers` that is already sorted in non-decreasing order,  
find two numbers such that they add up to a specific target number.

Let these two numbers be `numbers[index1]` and `numbers[index2]`  
where `1 <= index1 < index2 <= numbers.length`.

Return the indices of the two numbers, **added by one**, as an integer array `[index1, index2]` of length 2.

The tests are generated such that there is **exactly one solution**,  
and you may **not use the same element twice**.

Your solution must use only **constant extra space**.

---

## 💻 Example

**Example 1:**  
**Input:** `numbers = [2,7,11,15], target = 9`  
**Output:** `[1,2]`  
**Explanation:** The sum of 2 and 7 is 9 → index1 = 1, index2 = 2.

**Example 2:**  
**Input:** `numbers = [2,3,4], target = 6`  
**Output:** `[1,3]`  
**Explanation:** The sum of 2 and 4 is 6 → index1 = 1, index2 = 3.

**Example 3:**  
**Input:** `numbers = [-1,0], target = -1`  
**Output:** `[1,2]`  
**Explanation:** The sum of -1 and 0 is -1 → index1 = 1, index2 = 2.

---

## 🧠 My Approach
I used the **Two Pointer** approach because the array is **sorted**.

- Start with two pointers:  
  - `l` (left) = 0  
  - `r` (right) = numbers.size() - 1  
- Calculate `sum = numbers[l] + numbers[r]`.  
- If `sum == target`, return `{l + 1, r + 1}` (since the array is 1-indexed).  
- If `sum < target`, move the left pointer right (`l++`).  
- If `sum > target`, move the right pointer left (`r--`).  
- Continue until the pair is found.

---

🕒 Time Complexity:  

The array is traversed at most once using two pointers → O(n)

💾 Space Complexity:   

Only a few variables used → O(1)

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int l = 0, r = numbers.size() - 1;
        while (l < r) {
            int sum = numbers[l] + numbers[r];
            if (sum == target) {
                return {l + 1, r + 1};
            }
            if (sum < target) {
                l++;
            } else {
                r--;
            }
        }
        return {};
    }
};
