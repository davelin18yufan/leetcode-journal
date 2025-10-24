# 1790. Check if One String Swap Can Make Strings Equal

**Difficulty:** Easy  
**Algorithm:** String  
**Data Structure:** Hash Table  
**Date:** 2025-10-24  

---

## 📝 Problem Description
Given two strings `s1` and `s2` of equal length, determine if you can make them equal by performing at most one string swap on exactly one of the strings. A string swap consists of choosing two indices in a string and swapping the characters at those indices.

---

## Real-world analogy
Imagine you have two bookshelves, `s1` and `s2`, that are supposed to be identical, but a single pair of books might have been swapped on one shelf. Your task is to verify if this is the case. You walk along both shelves, comparing books at each position. If you find more than two positions where the books don't match, you know it's impossible to fix with a single swap. If you find exactly two mismatched positions, you check if swapping the books at these two positions on one shelf makes it identical to the other. If so, they are "almost equal."

---

## 💡 Key Idea
The core idea is to count the number of positions where the characters in `s1` and `s2` differ.
1. If the strings are already equal, no swap is needed, so they are almost equal.
2. If there is one difference, it's impossible to make them equal with one swap.
3. If there are two differences, say at indices `i` and `j`, we must check if swapping `s1[i]` with `s1[j]` results in `s2`. This is equivalent to checking if `s1[i] == s2[j]` and `s1[j] == s2[i]`.
4. If there are more than two differences, it's impossible to make them equal with a single swap.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the length of the strings, because we iterate through them once.
- Space: `O(1)`, as we only use a small, constant amount of extra space to store the indices of the differences.

---

## 📖 Notes
- This problem is a good example of handling string comparison with a limited number of allowed modifications.
- The most efficient approach is to track the indices of the differing characters rather than just the characters themselves, as this preserves the positional information needed to verify the swap.
