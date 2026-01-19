# 🧩 Problem: Is Subsequence

You can read the problem description [here](https://leetcode.com/problems/is-subsequence/).

## 📄 Problem Statement
Given two strings `s` and `t`, return `true` if `s` is a subsequence of `t`, otherwise return `false`.

A subsequence is formed by deleting some characters (or none) from the original string without changing the relative order of the remaining characters.

---

## 💻 Examples

Example 1:
Input: `s = "abc", t = "ahbgdc"`  
Output: `true`

Example 2: 
Input:`s = "axc", t = "ahbgdc"`  
Output:`false`

---

## 🧠 My Approach
I used a **recursive approach** with two pointers.

- Pointer `i` is used to track the current character of string `s`.
- Pointer `j` is used to traverse string `t`.
- If characters at `s[i]` and `t[j]` match, I move `i` forward.
- I always move `j` forward to keep checking the remaining characters.
- If all characters of `s` are matched (`i` reaches the end), I return `true`.
- If `t` finishes before `s`, I return `false`.

---

## ⚙️ Code (C++)
```cpp
class Solution {
private:
    bool solve(const string &s, const string &t, int i, int j) {
        // Base cases
        if (i >= s.size()) return true;
        if (j == t.size()) return false;

        if (s[i] == t[j]) i++;

        // Recursive call
        return solve(s, t, i, j + 1);
    }

public:
    bool isSubsequence(string s, string t) {
        return solve(s, t, 0, 0);
    }
};
