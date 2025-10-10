# 2563. Count the Number of Fair Pairs

**Difficulty:** Medium  
**Algorithm:** Two Pointers, Binary Search, Sorting  
**Data Structure:** Array  
**Date:** 2025-10-10  

---

## 📝 Problem Description
Given a 0-indexed integer array `nums` of size `n` and two integers `lower` and `upper`, return the number of fair pairs. A pair `(i, j)` is fair if `0 <= i < j < n` and `lower <= nums[i] + nums[j] <= upper`.

---

## Real-world analogy
Imagine you're a dance instructor trying to form dance pairs from a large group of students. Each student has a certain height (`nums`). You're looking for pairs `(i, j)` where their combined height is within a specific range, say between `lower` and `upper`. A brute-force approach would be to have every student pair up with every other student, which is very slow. A much faster way is to first have all students line up by height (sorting). Now, for any given student `i`, you know their ideal partner `j` must have a height within a specific range. Since the line is sorted, you can very quickly find the block of students who fit this criteria using a fast search method, without checking everyone.

---

## 💡 Key Idea
The key to solving this problem efficiently is to first sort the array. Instead of directly counting pairs within the range `[lower, upper]`, we can transform the problem into a more manageable one. The number of pairs in this range is equivalent to `(count of pairs with sum <= upper) - (count of pairs with sum <= lower - 1)`. This allows us to create a helper function that counts pairs with a sum less than or equal to a given target. This helper function can be implemented efficiently in O(N) time using the two-pointer technique on the sorted array.

---

## 🧮 Complexity Analysis
- Time: `O(N log N)` (dominated by the initial sort)
- Space: `O(log N)` or `O(N)` (depending on the space complexity of the sorting algorithm)

---

## 📖 Notes
- Real-world analogy: Finding dance pairs with a combined height in a specific range.
- Edge cases considered: empty array, `lower` > `upper`.
- The core trick is converting `count(lower <= sum <= upper)` into `count(sum <= upper) - count(sum <= lower - 1)`.
