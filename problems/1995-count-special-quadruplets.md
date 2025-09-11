# 1995. Count Special Quadruplets

**Difficulty:** Easy
**Algorithm:** Hash Table, Enumeration
**Data Structure:** Hash Table
**Date:** 2025-09-11

---

## 📝 Problem Description

Given a 0-indexed integer array `nums`, your task is to find the number of unique quadruplets `(a, b, c, d)` that satisfy two conditions:
1. `nums[a] + nums[b] + nums[c] == nums[d]`
2. `a < b < c < d`

---

## 💡 Key Idea

The problem asks for a count of specific combinations, which immediately suggests nested loops. A brute-force approach using four nested loops for `a`, `b`, `c`, and `d` would result in an O(N⁴) time complexity, which is likely too slow given the constraints.

The key to optimization is to reduce one of the loops to a constant-time lookup. We can rewrite the equation as `nums[a] + nums[b] + nums[c] = nums[d]`. If we fix `a`, `b`, and `c`, we need a quick way to check how many times the `sum` appears at an index `d` where `d > c`.

A more efficient O(N³) approach involves iterating backwards. We can fix `c` and iterate through all `a` and `b` to its left (`a < b < c`). As we iterate `c` from right to left, we maintain a frequency map of all numbers to its right.

The algorithm is as follows:
1. Initialize `count = 0` and a frequency map `freq`.
2. Iterate `c` from `n-2` down to `2`.
3. Before the inner loops, add `nums[c+1]` to the frequency map. This map will always contain the counts of elements `nums[d]` where `d > c`.
4. For the fixed `c`, iterate through all possible pairs `a` and `b` to its left (`a` from `0` to `c-1`, `b` from `a+1` to `c-1`).
5. Calculate `sum = nums[a] + nums[b] + nums[c]`.
6. Check the frequency map for this `sum`. If it exists, it means we found valid `d`'s, so we add its frequency to our `count`.

This trades O(N) space for the map to reduce the time complexity from O(N⁴) to O(N³), which is efficient enough for the given constraints.

---

## 🧮 Complexity Analysis

- **Time:** O(N³) - We have three nested loops to iterate through `c`, `b`, and `a`. The map operations inside are O(1) on average.
- **Space:** O(N) - In the worst case, the frequency map may need to store every unique number in the array.

---

## 📖 Notes

- **Real-world analogy:** Imagine you're at a food court with a menu where every item has a price (`nums`). You need to find out how many different ways you can pick **three cheaper items** (`a`, `b`, `c`) whose total price exactly equals the price of a **fourth, more expensive item** (`d`) that appears later on the menu. The optimized solution avoids re-scanning the expensive items for every combination of three by keeping a running tally (the frequency map) of the prices of expensive items seen so far.

- **Edge cases considered:** The constraints state `nums.length` is between 4 and 50, so we don't need to worry about arrays with fewer than 4 elements. The values are small, so integer overflow is not a concern.
