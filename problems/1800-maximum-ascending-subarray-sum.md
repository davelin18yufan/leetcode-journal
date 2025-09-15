# 1800. Maximum Ascending Subarray Sum

**Difficulty:** Easy
**Algorithm:** Single Pass
**Data Structure:** Array
**Date:** 2025-09-15

---

## 📝 Problem Description

Imagine analyzing daily stock prices to find the most profitable period of uninterrupted growth. The goal is to find a continuous series of days where the price consistently increased and calculate the total value of that streak.

---

## 💡 Key Idea

The core idea is to iterate through the array once. We use a `currentSum` variable to track the sum of the current ascending streak. If the current number is greater than the previous one, we add it to `currentSum`. If the streak is broken (the current number is not greater), we reset `currentSum` to the value of the current number. A separate `maxSum` variable is maintained and updated whenever `currentSum` becomes larger than it, ensuring we always hold the maximum sum found so far.

---

## 🧮 Complexity Analysis

- **Time:** O(N), as we only iterate through the input array once.
- **Space:** O(1), as we only use a few variables to store state, regardless of the input size.

---

## 📖 Notes

- **Real-world analogy:** Finding the most profitable continuous growth period in stock market data.
- **Edge cases considered:** An empty or single-element array, and an array that is entirely in descending order.
- The solution is already optimal in both time and space complexity.
