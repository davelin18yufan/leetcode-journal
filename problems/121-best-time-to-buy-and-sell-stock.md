# 121. Best Time to Buy and Sell Stock

**Difficulty:** Easy  
**Algorithm:** Dynamic Programming, Greedy  
**Data Structure:** Array  
**Date:** 2025-12-20  

---

## 📝 Problem Description
You are given an array `prices` where `prices[i]` is the price of a given stock on the `i`th day. You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock. Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

---

## 🏢 Real-world analogy
Imagine you're developing a "Price Drop Tracker" for an e-commerce platform like Amazon. The system monitors a continuous stream of prices for a specific product. The goal is to identify the best theoretical profit one could have made by buying at a historical low point and selling at a later high point. The key constraint is that you can't travel back in time; you must make the buy decision before the sell decision. As you process the price history, you always need to remember the lowest price seen *so far* to calculate the potential profit for the current day.

---

## 💡 Key Idea
The most efficient approach is a one-pass **Greedy strategy**. As we iterate through the price array, we maintain two variables:
1.  `minPrice`: Keeps track of the lowest stock price encountered up to the current day.
2.  `maxProfit`: Stores the maximum profit found so far.

For each day's price, we first check if it's a new minimum. If it is, we update `minPrice`. If not, we calculate the potential profit by subtracting `minPrice` from the current price. If this profit is greater than `maxProfit`, we update `maxProfit`. This ensures we find the global maximum profit with a single scan.

---

## 🧮 Complexity Analysis
- Time: `O(N)` - We iterate through the array of prices once.
- Space: `O(1)` - We only use a few variables to store state, regardless of the input size.

---

## 📖 Notes
- Status: **Review Needed**. The user requested a mark for future review as it's not fully completed/mastered.
- The core logic is a greedy approach, often categorized under Dynamic Programming because the decision at each step depends on the optimal state of the subproblem (the minimum price seen before).
- Edge cases: an empty or single-element array (no transaction possible), or a continuously decreasing price list (profit is 0).
