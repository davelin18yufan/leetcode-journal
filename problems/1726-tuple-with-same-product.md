# 1726. Tuple with Same Product

**Difficulty:** Medium  
**Algorithm:** Hash Table, Counting  
**Data Structure:** Array  
**Date:** 2025-11-06  

---

## 📝 Problem Description
Given an array `nums` of distinct positive integers, find the number of tuples `(a, b, c, d)` such that `a * b = c * d` where `a`, `b`, `c`, and `d` are all distinct elements of `nums`.

---

## Real-world analogy
Imagine you are a jeweler with a collection of gems, each with a unique weight. You want to create pairs of gems for earrings. To ensure balance, the product of the weights of the two gems in each earring pair must be equal. You are looking for how many ways you can form two distinct pairs of gems that have the same weight product. For every two pairs you find, you can arrange them in 8 different ways on a display stand.

---

## 💡 Key Idea
The core idea is to find pairs of numbers `(a, b)` and `(c, d)` that have the same product. We can iterate through all possible pairs of numbers in the input array and calculate their product. A hash map is used to store the frequency of each product. For any product that occurs `n` times, we can choose 2 pairs out of `n` in `n * (n - 1) / 2` ways. Each such choice of two pairs can form 8 different tuples. Therefore, for a product that appears `n` times, it contributes `n * (n - 1) / 2 * 8 = n * (n - 1) * 4` tuples.

---

## 🧮 Complexity Analysis
- Time: `O(N^2)` 
- Space: `O(N^2)`

---

## 📖 Notes
- The problem is simplified by realizing that for every two pairs with the same product, there are always 8 possible tuple combinations.
- A hash map is crucial for efficiently counting the occurrences of each product.
