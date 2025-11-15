# 🔗🔤 Problem: Valid Anagram

You can read the problem description here : [Problem](https://leetcode.com/problems/valid-anagram/)

## Problem Statement
Given two strings `s` and `t`, return **true** if `t` is an **anagram** of `s`, and **false** otherwise.

---

## 💻 Example

**Example 1:**  
**Input:** `s = "anagram"`, `t = "nagaram"`  
**Output:** `true`

**Example 2:**  
**Input:** `s = "rat"`, `t = "car"`  
**Output:** `false`

---

## 🧠 My Approach
I used a **character frequency counting** approach to determine if both strings contain the same letters in the same quantities.

Steps:
- If the lengths of `s` and `t` are not equal → return `false`.
- Create a frequency vector of size `26` (for each lowercase letter).
- For each character in both strings:
  - Increment for `s[i]`.
  - Decrement for `t[i]`.
- Finally, if all frequency values are `0`, both strings are anagrams.

---

🕒 Time Complexity :

We iterate through both strings once → O(n)

💾 Space Complexity :

We use a frequency array of size 26 → O(1)

---

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        if (s.size() != t.size()) {
            return false;
        }

        vector<int> count(26, 0);
        for (int i = 0; i < s.size(); i++) {
            count[s[i] - 'a']++;
            count[t[i] - 'a']--;
        }

        for (int c : count) {
            if (c != 0) return false;
        }
        return true;
    }
};
