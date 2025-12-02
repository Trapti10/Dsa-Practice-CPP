# 🔍 Search a 2D Matrix II

You can read the problem description here : [Problem](https://leetcode.com/problems/search-a-2d-matrix-ii/).

## 🧩 Problem Statement
Write an efficient algorithm to search for a value `target` in an `m x n` integer matrix.  
The matrix has the following properties:

- Each row is sorted in **ascending** order (left → right).  
- Each column is sorted in **ascending** order (top → bottom).

---

## 📘 Examples

### **Example 1**
**Input:**  
`matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 5`  
**Output:** `true`

### **Example 2**
**Input:**  
`matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 20`  
**Output:** `false`

---

## 🧠 My Approach
I started the search from the **top-right corner** of the matrix:

- If the current element equals the target → return `true`
- If the current element is **greater than** the target → move **left** (decrease column)
- If it is **smaller** → move **down** (increase row)

This works because rows and columns are sorted, so we eliminate one full row or column in each step.

---

⏱️ Time Complexity

We move at most m + n steps → O(m + n)

💾 Space Complexity

No extra data structures → O(1)

---

## 💻 Code (C++)
```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int m = matrix.size();
        int n = matrix[0].size();
        int row = 0;
        int col = n - 1;

        while (row < m && col >= 0) {
            if (target == matrix[row][col]) {
                return true;
            }
            else if (target < matrix[row][col]) {
                col--;
            }
            else {
                row++;
            }
        }
        return false;
    }
};
