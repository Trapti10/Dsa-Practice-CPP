# 🧩 Problem: Letter Combinations of a Phone Number

You can read the problem description [here](https://leetcode.com/problems/letter-combinations-of-a-phone-number/).

## 📄 Problem Statement
Given a string `digits` containing digits from **2 to 9**, return all possible letter combinations that the number could represent based on the phone keypad mapping.  
Return the answer in **any order**.

---

## 💻 Examples

Example 1:
Input: `digits = "23"`  
Output: `["ad","ae","af","bd","be","bf","cd","ce","cf"]`

Example 2: 
Input: `digits = "2"`  
Output: `["a","b","c"]`

---

## 🧠 My Approach
I solved this problem using **recursion and backtracking**.

- Each digit maps to some characters (like on a phone keypad).
- I process the digits one by one and try all possible letters for the current digit.
- I keep adding characters to a temporary string `output`.
- When the index reaches the end of the digit string, I store the formed combination.
- After each recursive call, I remove the last character (backtracking) to try other possibilities.

This ensures all valid combinations are generated.

---

## ⚙️ Code (C++)
```cpp
class Solution {
private:
    void solve(string digit, string output, int index, vector<string>& ans, string mapping[]) {
        // Base case
        if (index >= digit.size()) {
            ans.push_back(output);
            return;
        }

        int number = digit[index] - '0';
        string value = mapping[number];

        for (int i = 0; i < value.length(); i++) {
            output.push_back(value[i]);
            solve(digit, output, index + 1, ans, mapping);
            output.pop_back();
        }
    }

public:
    vector<string> letterCombinations(string digits) {
        vector<string> ans;
        if (digits.length() == 0) return ans;

        string output;
        int index = 0;
        string mapping[10] = {"", "", "abc", "def", "ghi", "jkl",
                              "mno", "pqrs", "tuv", "wxyz"};

        solve(digits, output, index, ans, mapping);
        return ans;
    }
};
