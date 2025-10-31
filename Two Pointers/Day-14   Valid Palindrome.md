# 🔗🔤 Problem: Valid Palindrome

You can read the problem description here : [ Problem](https://leetcode.com/problems/valid-palindrome/)

## Problem Statement
A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward.  

Alphanumeric characters include letters and numbers.  

Given a string `s`, return `true` if it is a palindrome, or `false` otherwise.

---

## 💻 Example

**Example 1:**  
**Input:** `s = "A man, a plan, a canal: Panama"`  
**Output:** `true`  
**Explanation:** `"amanaplanacanalpanama"` is a palindrome.  

**Example 2:**  
**Input:** `s = "race a car"`  
**Output:** `false`  
**Explanation:** `"raceacar"` is not a palindrome.  

**Example 3:**  
**Input:** `s = " "`  
**Output:** `true`  
**Explanation:** After removing non-alphanumeric characters, `s` becomes an empty string `""`, which is a palindrome.  

---

## 🧠 My Approach
I used the **Two Pointer technique** with **character validation**:  
- Initialize two pointers, `l` at the start and `r` at the end of the string.  
- Move both pointers toward each other.  
- Skip characters that are not alphanumeric using a helper function.  
- Compare lowercase versions of `s[l]` and `s[r]`.  
- If any mismatch occurs → return `false`.  
- If all valid characters match → return `true`.

---

🕒 Time Complexity:

We iterate through the string once with two pointers → O(n)

💾 Space Complexity:

Only a few extra variables used → O(1)

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    bool isAlphaNum(char ch){
        if((ch >= '0' && ch <= '9') || (tolower(ch) >= 'a' && tolower(ch) <= 'z')){
            return true;
        }
        return false;
    }

    bool isPalindrome(string s) {
        int n = s.length();
        int l = 0, r = n - 1;

        while (l < r) {
            if (!isAlphaNum(s[l])) {
                l++;
                continue;
            }
            if (!isAlphaNum(s[r])) {
                r--;
                continue;
            }
            if (tolower(s[l]) != tolower(s[r])) {
                return false;
            }
            l++;
            r--;
        }
        return true;
    }
};
