# 2516. Take K of Each Character From Left and Right

**Difficulty:** Medium  
**Algorithm:** Sliding Window  
**Data Structure:** Hash Table  
**Date:** 2025-10-29  

---

## 📝 Problem Description

Given a string `s` consisting of only the characters 'a', 'b', and 'c', and an integer `k`, you need to take at least `k` of each character from either the left or right end of the string. The goal is to find the minimum number of characters you have to take.

---

## Real-world analogy

Imagine you have a long string of 'a', 'b', 'c' beads. You need to gather `k` of each. You can only take beads from the left end or the right end. The smart way to solve this is to not think about what to take, but what to *leave*. The problem transforms into finding the longest middle part of the string that you can leave behind, which still allows you to gather the required `k` of each bead from the ends. Once you find this longest "leave-behind" window, the answer is simply the total length of the string minus the length of this window.

---

## 💡 Key Idea

The key is to **invert the problem**: instead of minimizing the characters *taken*, we maximize the *middle subarray* we *leave*.

If the string has `total_a` 'a's, and we need to *take* `k` 'a's, we must *leave* at most `total_a - k` 'a's in the middle part. This gives us a condition for a sliding window. We can find the longest subarray that respects these "leave-behind" counts for 'a', 'b', and 'c'. The minimum number of characters to take is then `s.length - maxLength` of this valid subarray.

---

## 🧮 Complexity Analysis

- Time: `O(N)` 
- Space: `O(1)`

---

## 📖 Notes

- Real-world analogy: Imagine collecting a specific number of different colored beads from the ends of a long string; the most efficient way is to determine the largest possible middle section of beads you can leave behind.
- This problem is a classic example of "inverting the problem" combined with the sliding window technique.
