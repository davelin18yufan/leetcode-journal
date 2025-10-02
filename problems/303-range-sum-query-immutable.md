# 303. Range Sum Query - Immutable

**Difficulty:** Easy  
**Algorithm:** Prefix Sum  
**Data Structure:** Array, Design  
**Date:** 2025-10-02  

---

## 📝 Problem Description
Given an integer array `nums`, handle multiple queries of the following type: calculate the sum of the elements of `nums` between indices `left` and `right` inclusive where `left <= right`.

---

## Real-world analogy
Imagine you're on a long road trip, and at the end of each day, you write down how many miles you drove that day. This is your `nums` array. Now, imagine your friend, who is terrible at math, repeatedly asks you, "How many miles did we drive between Day 5 and Day 10?"

A naive approach would be to add the miles for each day in the range every time. A smarter way is to create a "Cumulative Mileage" log beforehand. To find the miles driven between Day 5 and Day 10, you simply take the total miles by the end of Day 10 and subtract the total miles by the end of Day 4. This is the Prefix Sum pattern, allowing for instant answers to any range query after a one-time setup.

---

## 💡 Key Idea
The core insight is to trade-off a one-time preprocessing cost to achieve constant-time query responses. By pre-calculating a `prefixSums` array in the constructor, where `prefixSums[i]` stores the sum of all elements from the start of the original array up to index `i-1`, we can answer any range sum query `[left, right]` with a single subtraction: `prefixSums[right + 1] - prefixSums[left]`.

---

## 🧮 Complexity Analysis
- Time:
  - `constructor`: `O(N)` to build the prefix sum array.
  - `sumRange`: `O(1)` for the query.
- Space: `O(N)` to store the prefix sum array.

---

## 📖 Notes
- Real-world analogy: Calculating daily mileage totals on a road trip to quickly find the distance traveled over any period.
- This pattern is ideal for scenarios with frequent range sum queries on an immutable dataset.
