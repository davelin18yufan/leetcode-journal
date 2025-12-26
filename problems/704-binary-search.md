# 704. Binary Search

**Difficulty:** Easy  
**Algorithm:** Binary Search  
**Data Structure:** Array  
**Date:** 2025-12-26  

---

## 📝 Problem Description
Given a sorted array of integers `nums` and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return -1. You must write an algorithm with `O(log n)` runtime complexity.

---

## Real-world analogy
Imagine you're looking for a specific book in a library where all the books are sorted by their call number. Instead of checking every single book from the beginning (a linear search), you would likely go to the middle of the shelf. If the call number you see is higher than the one you're looking for, you know your book must be in the first half. If it's lower, you'll focus on the second half. You repeat this process of halving the search area until you find the book. This is the core idea of binary search, making it incredibly efficient for finding items in large, sorted datasets like database indexes or dictionary lookups.

---

## 💡 Key Idea
The core insight is to leverage the sorted nature of the array. By using two pointers, `left` and `right`, to define the current search range, we can calculate the middle index. If the middle element is the target, we've found it. If the middle element is less than the target, we know the target must be in the right half, so we discard the left half by moving the `left` pointer. If it's greater, we discard the right half by moving the `right` pointer. This "divide and conquer" approach reduces the search space by half in each step.

---

## 🧮 Complexity Analysis
- Time: `O(log N)` 
- Space: `O(1)`

---

## 📖 Notes
- Real-world analogy: Efficiently searching for a record in a database using an indexed column.
- This solution was not fully completed and requires further review.
- The standard template using `left <= right` is generally preferred to avoid edge case issues and potential infinite loops.
