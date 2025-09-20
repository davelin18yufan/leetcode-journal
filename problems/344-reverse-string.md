# 344. Reverse String

**Difficulty:** Easy  
**Algorithm:** Two Pointers  
**Data Structure:** String  
**Date:** 2025-09-20  

---

## 📝 Problem Description
The task is to reverse a given string, which is provided as an array of characters. The modification must be done in-place, meaning no extra array should be allocated for the solution, and it must be solved with O(1) extra memory.

---

## Real-world analogy
Think of reversing a row of books on a shelf. The most efficient way to do it with two people is:

1.  One person stands at the beginning (`start` pointer) and another person stands at the end (`end` pointer).
2.  They both pick up the book in front of them.
3.  They **swap books** and place them back on the shelf.
4.  Both people then take one step toward the middle and repeat the process.
5.  They stop when they meet or cross paths in the middle.

This physical process is exactly what the two-pointer algorithm does in memory. It's the most direct way to solve the problem by only touching each element once.

---

## 💡 Key Idea
The core idea is to use a **two-pointer technique**. One pointer starts at the beginning of the array and the other at the end. In a loop, the elements at the pointer locations are swapped, and the pointers are moved towards the center until they meet. This guarantees that every character is swapped with its counterpart from the other end of the string, effectively reversing it.

---

## 🧮 Complexity Analysis
- Time: `O(N)` where N is the number of characters, as we iterate through roughly half of the array.
- Space: `O(1)` because the reversal is done in-place, using only a constant amount of extra memory for the pointers and a temporary variable for the swap.

---

## 📖 Notes
- Real-world analogy: Reversing a row of books on a shelf by swapping from both ends.
- This problem is a classic example of the two-pointer pattern, which is fundamental for solving many array and string manipulation problems efficiently.
