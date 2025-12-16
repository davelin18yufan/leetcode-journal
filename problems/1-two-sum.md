# 1. Two Sum

**Difficulty:** Easy
**Algorithm:** Hash Table
**Data Structure:** Array
**Date:** 2025-12-16

---

## 📝 Problem Description
Given an integer array nums and a target value target, find two integers in the array whose sum equals the target, and return their indices.

---

## Real-world analogy
This is like organizing a pile of shopping receipts and trying to find two receipts whose total amount exactly matches a specific budget. If you compare them one by one (brute force), it becomes very time-consuming when there are many receipts. But if you have a smart assistant (a hash map), every time you look at a new receipt, you ask the assistant to remember “how much is still needed to reach the budget.” When you later see another receipt, you simply ask: “Is this amount something you were waiting for?” If yes, you’ve immediately found the two matching receipts—without digging through the old pile again. This smart assistant greatly improves efficiency.

---

## 💡 Key Idea
Use a one-pass hash map approach. While iterating through the array, compute the difference diff between the target and the current element. First, check whether diff already exists in the hash map. If it does, you’ve found the solution and can return the result immediately. If not, store the current element and its index in the hash map. This guarantees the solution is found in a single pass and avoids using the same element twice.

---

## 🧮 Complexity Analysis
- Time: `O(N)`
- Space: `O(N)`

---

## 📖 Notes
- The initial idea is usually a double loop (brute force), which has a time complexity of O(n²). An improvement is to first build a hash map and then search (two-pass), achieving O(n). The optimal solution combines both steps into a single pass, reducing the constant factor from O(2n) to O(n) and resulting in cleaner code.

- Real-world applications include quickly matching transactions in financial systems or finding complementary data pairs in databases.
