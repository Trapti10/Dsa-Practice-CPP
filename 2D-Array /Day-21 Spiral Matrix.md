# 🔗 🧩 Problem: Spiral Matrix

You can read the problem description here : [Problem](https://leetcode.com/problems/spiral-matrix/).

## Problem Statement
Given an `m x n` matrix, return all elements of the matrix in **spiral order**.

---

## 💻 Examples 

**Example 1:**  
Input: `matrix = [[1,2,3],[4,5,6],[7,8,9]]`  
Output: `[1,2,3,6,9,8,7,4,5]`

**Example 2:**  
Input: `matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]`  
Output: `[1,2,3,4,8,12,11,10,9,5,6,7]`

---

## 🧠 My Approach
I solved this problem by simulating the spiral traversal using four boundaries:

- `startingRow`, `endingRow`
- `startingCol`, `endingCol`

At every step:
- Move left → right (top row)
- Move top → bottom (right column)
- Move right → left (bottom row)
- Move bottom → top (left column)

After completing each direction, I update the corresponding boundary so that the spiral closes inward.  
A `count` variable tracks how many elements are added to avoid accessing out-of-bound indices.

---

🕒 Time Complexity

Every element is visited once → O(m × n)

💾 Space Complexity

Output array only → O(1) extra space (excluding result)

---

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> ans;

        int row = matrix.size();
        int col = matrix[0].size();

        int count = 0;
        int total = row * col;

        int startingRow = 0;
        int startingCol = 0;
        int endingRow = row - 1;
        int endingCol = col - 1;

        while(count < total){
            // print starting row
            for(int i = startingCol; i <= endingCol && count < total; i++){
                ans.push_back(matrix[startingRow][i]);
                count++;
            }
            startingRow++;

            // print ending column
            for(int i = startingRow; i <= endingRow && count < total; i++){
                ans.push_back(matrix[i][endingCol]);
                count++;
            }
            endingCol--;

            // print ending row
            for(int i = endingCol; i >= startingCol && count < total; i--){
                ans.push_back(matrix[endingRow][i]);
                count++;
            }
            endingRow--;

            // print starting column
            for(int i = endingRow; i >= startingRow && count < total; i--){
                ans.push_back(matrix[i][startingCol]);
                count++;
            }
            startingCol++;
        }

        return ans;
    }
};
