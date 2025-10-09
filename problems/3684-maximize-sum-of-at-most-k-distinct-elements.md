# 3684. Maximize Sum of At Most K Distinct Elements

**Difficulty:** Easy  
**Algorithm:** Greedy, Sorting  
**Data Structure:** Array, Hash Table  
**Date:** 2025-10-09  

---

## 📝 Problem Description
Given an integer array `nums` and an integer `k`, the task is to select at most `k` distinct elements from the array such that their sum is maximized. The function should return the sum of these elements.

---

## Real-world analogy
This problem is like packing a small treasure chest to maximize its value.

  * You have a pile of treasures with various values (`nums`), and some treasures are duplicates (e.g., multiple gold coins of the same value).
  * Your treasure chest can only hold `k` items.
  * A special rule: you are not allowed to put two identical items in the chest (the chosen numbers must be **distinct**).

To maximize the value in your chest, your strategy would be to lay out one of each unique treasure type, sort them from most to least valuable, and then simply pick the top `k` treasures for your chest.

---

## 💡 Key Idea
The optimal strategy is a greedy one. To maximize the sum, we must choose the largest available numbers. Since the chosen elements must be distinct, the first step is to filter out any duplicates. This can be efficiently done using a `Set`. After obtaining the unique numbers, we sort them in descending order and pick the first `k` elements. Their sum will be the maximum possible.

---

## 🧮 Complexity Analysis
- Time: `O(N log N)`, dominated by the sorting operation on the unique elements.
- Space: `O(U)`, where U is the number of unique elements, for storing the set and the sorted array.

---

## 📖 Notes
- Real-world analogy: Packing a treasure chest with the most valuable, unique items.
- The core logic combines creating a `Set` for uniqueness, `sort` for the greedy choice, and `slice` to limit the count to `k`.
