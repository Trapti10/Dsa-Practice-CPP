# 🔗🧩 Problem: Permutation in String

You can read the problem description here : [Problem](https://leetcode.com/problems/permutation-in-string/).

##  Problem Statement
Given two strings `s1` and `s2`, return `true` if **s2 contains any permutation of s1**, otherwise return `false`.

In simple terms, we check whether *any rearrangement of s1 exists as a substring inside s2*.

---

## 💻 Examples

**Example 1:**  
Input: `s1 = "ab"`, `s2 = "eidbaooo"`  
Output: `true`  
Explanation: `"ba"` is a permutation of `"ab"` and appears in `s2`.

**Example 2:**  
Input: `s1 = "ab"`, `s2 = "eidboaoo"`  
Output: `false`

---

## 🧠 My Approach
I solved this using the **sliding window + frequency counting** technique:

- First, count the frequency of all characters in `s1`.
- Then, use a sliding window of size `s1.length()` on `s2`.
- For each window, maintain a frequency array for characters in the window.
- After forming each window, compare the frequency arrays:
  - If they match, it means this window is a permutation of `s1`.
- Move the window by adding a new character and removing the previous one.

This approach is efficient and avoids generating all permutations.

---

🕒 Time Complexity

Sliding window across s2: O(n)

Comparing frequency arrays each time: O(26) → constant
Overall: O(n)

💾 Space Complexity

Two frequency arrays of size 26 → O(1) constant space

---

## ⚙️ Code (C++)
```cpp
class Solution {
private:
    bool checkEqual(int a[26], int b[26]){   
        for(int i = 0; i < 26; i++){
            if(a[i] != b[i]){
                return false;
            }
        }
        return true;
    }

public:
    bool checkInclusion(string s1, string s2) {

        int count1[26] = {0};
        for(int i = 0; i < s1.length(); i++){
            int index = s1[i] - 'a';
            count1[index]++;
        }
        
        int windowLength = s1.length();
        int count2[26] = {0};
        int i = 0;

        while(i < windowLength && i < s2.length()){
            int index = s2[i] - 'a';
            count2[index]++;
            i++;
        }

        if(checkEqual(count1, count2)){
            return true;
        }
        
        while(i < s2.length()){
            char newChar = s2[i];
            count2[newChar - 'a']++;
            
            char oldChar = s2[i - windowLength];
            count2[oldChar - 'a']--;
            
            i++;

            if(checkEqual(count1, count2)){
                return true;
            }
        }

        return false;
    }
};
