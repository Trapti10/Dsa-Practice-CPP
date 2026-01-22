# 🧩 Problem: Second Largest Digit in a String

You can read the problem description [here](https://leetcode.com/problems/second-largest-digit-in-a-string/).

## 📄 Problem Statement
Given an alphanumeric string `s`, return the **second largest numerical digit** that appears in `s`, or `-1` if it does not exist.  
An alphanumeric string contains lowercase English letters and digits. :contentReference[oaicite:0]{index=0}

---

## 💻 Example

Example 1:
Input: `s = "dfa12321afd"`  
Output: `2`  
Explanation: The digits that appear in the string are `[1, 2, 3]`. The second largest digit is `2`. :contentReference[oaicite:1]{index=1}

Example 2: 
Input: `s = "abc1111"`  
Output: `-1`  
Explanation: The digits that appear in the string are `[1]`. There is no second largest digit. :contentReference[oaicite:2]{index=2}

---

## 🧠 My Approach
First, I kept two variables `largest` and `secondLargest` initialized to `-1`.  
I then traversed the string character by character and checked if a character was a digit. If it was, I converted it to its numeric value.  
- If this value was greater than `largest`, I updated `secondLargest` to the old `largest` and `largest` to the new value.  
- Otherwise, if the value was **between `largest` and `secondLargest`**, I updated `secondLargest` only.  
At the end, `secondLargest` holds the answer or remains `-1` if no second largest digit exists.

---

🕒 Time Complexity
We traverse the string once → O(n), where n is the length of the string. 
Leetcode

💾 Space Complexity
Only two integer variables are used → O(1).

---

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    int secondHighest(string s) {
        int largest = -1, secondLargest = -1;
        
        for (char c : s) {
            if (isdigit(c)) {
                int value = c - '0';
                if (value > largest) {
                    secondLargest = largest;
                    largest = value;
                } else if (value > secondLargest && value < largest) {
                    secondLargest = value;
                }
            }
        }
        
        return secondLargest;
    }
};
