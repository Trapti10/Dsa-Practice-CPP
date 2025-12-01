# 🔗🧩 Search a 2D Matrix

You can read the problem description here : [Problem](https://leetcode.com/problems/search-a-2d-matrix/).

##  Problem Statement
You are given an `m x n` integer matrix with the following properties:

- Each row is sorted in non-decreasing order.  
- The first integer of each row is greater than the last integer of the previous row.

Given a `target`, return `true` if the target exists in the matrix, otherwise return `false`.

You must write a solution in **O(log(m * n))** time complexity.

---

## 💻 Examples

**Example 1:**  
Input: `matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3`  
Output: `true`

**Example 2:**  
Input: `matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13`  
Output: `false`

---

## 🧠 My Approach
I treated the entire 2D matrix as if it were a single sorted 1D array.  
- Start with two pointers: `s = 0` and `e = (rows * cols) - 1`.  
- Calculate `mid`, and convert it back to 2D using:  
  - `row = mid / cols`  
  - `col = mid % cols`  
- Compare the element with the target and adjust pointers like binary search.  
- This lets us perform an efficient search across the whole matrix.

---

🕒 Time Complexity

Binary search on m * n elements → O(log(m * n))

💾 Space Complexity

Only a few variables → O(1)

---

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int row = matrix.size();
        int col = matrix[0].size();
        int s = 0;
        int e = row * col - 1;

        int mid = s + (e - s) / 2;

        while (s <= e) {
            int element = matrix[mid / col][mid % col];

            if (element == target) {
                return true;
            }
            else if (element < target) {
                s = mid + 1;
            }
            else {
                e = mid - 1;
            }

            mid = s + (e - s) / 2;
        }
        return false;
    }
};
