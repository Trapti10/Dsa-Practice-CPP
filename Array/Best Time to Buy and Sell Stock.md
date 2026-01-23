# 🧩 Problem: Best Time to Buy and Sell Stock

You can read the problem description [here](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/).

## 📄 Problem Statement
You are given an array `prices` where `prices[i]` represents the stock price on the `iᵗʰ` day.  
You want to maximize your profit by choosing **one day to buy** and **a later day to sell**.  
Return the maximum profit you can achieve. If no profit is possible, return `0`.

---

## 💻 Examples

**Example 1:**  
**Input:** `prices = [7,1,5,3,6,4]`  
**Output:** `5`  
**Explanation:** Buy at price `1` and sell at price `6`.

**Example 2:**  
**Input:** `prices = [7,6,4,3,1]`  
**Output:** `0`  
**Explanation:** Prices keep decreasing, so no profit is possible.

---

## 🧠 My Approach
I solved this problem using a **single traversal** approach.

- I keep track of the **minimum price** seen so far.
- For each day, I calculate the profit if I sell on that day.
- I update the maximum profit whenever I find a better one.
- This ensures the buy happens before the sell.

At the end, the maximum profit is returned.

---

🕒 Time Complexity: 
The array is traversed once → O(n), where n is the number of days.

💾 Space Complexity: 
Only constant extra space is used → O(1).

---

## ⚙️ Code (C++)
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        int minPrice = prices[0];
        int maxPrice = 0;
        
        for(int i = 0; i < n; i++) {
            minPrice = min(prices[i], minPrice);
            maxPrice = max(maxPrice, prices[i] - minPrice);
        }
        
        return maxPrice;
    }
};
