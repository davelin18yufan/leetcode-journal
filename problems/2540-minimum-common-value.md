# 2540. Minimum Common Value

**Difficulty:** Easy  
**Algorithm:** Two Pointers  
**Data Structure:** Array  
**Date:** 2025-10-27  

---

## 📝 Problem Description
Given two integer arrays `nums1` and `nums2`, sorted in non-decreasing order, return the minimum integer common to both arrays. If there is no common integer, return -1.

---

## Real-world analogy
Imagine you have two sorted phone books, Book A (`nums1`) and Book B (`nums2`). You need to find the first name that appears in both books. The most efficient way is to open both books to the first page and compare the names. If the name in Book A comes alphabetically before the name in Book B, you turn the page in Book A. If the name in Book B comes first, you turn the page in Book B. You repeat this until you find a match or run out of names in one of the books. This avoids needing to create a separate checklist of all names in one book before checking the other.

---

## 💡 Key Idea
Since both arrays are sorted, we can use a **two-pointer** approach to find the common minimum value in a single pass. Initialize a pointer for each array at the beginning. Compare the elements at both pointers. If the element in the first array is smaller, move its pointer forward. If the element in the second array is smaller, move its pointer forward. If the elements are equal, that's the minimum common value. This is more space-efficient than using a hash set.

---

## 🧮 Complexity Analysis
- Time: `O(N + M)`, where N and M are the lengths of `nums1` and `nums2`. Each pointer traverses its respective array at most once.
- Space: `O(1)`, as we only use a constant amount of extra space for the pointers.

---

## 📖 Notes
- Real-world analogy: Finding the first common entry in two sorted lists, like phone books or schedules.
- Edge cases considered: one or both arrays are empty, no common elements. The two-pointer approach handles these gracefully.
