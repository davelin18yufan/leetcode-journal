# 1968. Array With Elements Not Equal to Average of Neighbors

**Difficulty:** Medium  
**Algorithm:** Greedy, Sorting  
**Data Structure:** Array  
**Date:** 2025-11-01  

---

## 📝 Problem Description
Given a 0-indexed integer array `nums`, rearrange the elements such that no element is equal to the average of its neighbors. More formally, for every `i` from `1` to `nums.length - 2`, `nums[i-1] + nums[i+1] / 2` is not equal to `nums[i]`.

---

## Real-world analogy
Imagine you are arranging a group of people of different heights in a line for a photograph. To create a visually interesting, non-uniform pattern, you want to avoid placing a person of average height directly between two people whose average height is exactly that person's height. For instance, you wouldn't want to place a 170cm person between a 160cm and an 180cm person.

A simple strategy to ensure this is to create a "zig-zag" or "peak-and-valley" arrangement. First, you sort everyone by height. Then, you pick the shortest person, then the tallest, then the second shortest, then the second tallest, and so on. This ensures that any person is standing next to people who are either both significantly taller or both significantly shorter than them, making it impossible for them to be the average of their neighbors.

---

## 💡 Key Idea
The core insight is that if we arrange the numbers in a "zig-zag" or "peak-and-valley" pattern, an element can never be the average of its neighbors. An element will either be a "peak" (larger than both neighbors) or a "valley" (smaller than both neighbors). A large number cannot be the average of two smaller numbers, and a small number cannot be the average of two larger numbers.

To achieve this, we first sort the input array `nums`. Then, using two pointers (`left` starting at the beginning and `right` at the end), we build a new array by alternately taking the smallest available element and the largest available element. This interleaving process naturally creates the desired zig-zag structure.

---

## 🧮 Complexity Analysis
- Time: `O(N log N)` due to the initial sorting of the array. The subsequent two-pointer traversal is `O(N)`.
- Space: `O(N)` to store the rearranged result array.

---

## 📖 Notes
- Real-world analogy: Arranging people by height in a "peak-and-valley" line to avoid visual mediocrity.
- Edge cases considered: The two-pointer logic naturally handles both odd and even length arrays.
