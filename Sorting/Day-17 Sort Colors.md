# 🔗 🎨 Problem: Sort Colors

You can read the problem description here : [Problem](https://leetcode.com/problems/sort-colors/)

##  Problem Statement
Given an array `nums` with `n` objects colored red, white, or blue, **sort them in-place** so that objects of the same color are adjacent, with the colors in the order **red, white, and blue**.  

We use the integers `0`, `1`, and `2` to represent the colors red, white, and blue, respectively.  

**You must solve this problem without using the library's sort function.**

---

## 💻 Example

**Example 1:**  
**Input:** `nums = [2,0,2,1,1,0]`  
**Output:** `[0,0,1,1,2,2]`  

**Example 2:**  
**Input:** `nums = [2,0,1]`  
**Output:** `[0,1,2]`  

---

## 🧠 My Approach
Here, I used **Bubble Sort** (in-place) to sort the array:

- Traverse the array from index `1` to `n-1`.
- For each element, compare adjacent elements.
- If `nums[j] > nums[j+1]`, swap them.
- If no swaps occur during a pass, the array is already sorted → break early.

> Note: This is not the most optimized solution for this problem, but it solves the task without using library sort functions.

---

🕒 Time Complexity

Worst case (Bubble Sort) → O(n²)
Best case (already sorted) → O(n)

💾 Space Complexity

In-place sorting → O(1)

---

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    void sortColors(vector<int>& nums) {
        for(int i = 1; i < nums.size(); i++){
            bool swapped = false;
            for(int j = 0; j < nums.size() - i; j++ ){
                if(nums[j] > nums[j+1]){
                    swap(nums[j], nums[j+1]);
                    swapped = true;
                }
            }
            if(swapped == false){
                break;
            }
        }
    }
};
