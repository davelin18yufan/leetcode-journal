# 3146. Permutation Difference between Two Strings

**Difficulty:** Easy  
**Algorithm:** Hash Table  
**Data Structure:** String  
**Date:** 2025-09-08  

---

## 📝 Problem Description
Given two strings, `s` and `t`, which are permutations of each other, find the sum of the absolute differences between the indices of each character in `s` and its corresponding index in `t`.

---

## 💡 Key Idea
The core idea is to first create a quick lookup map to store the index of each character in the string `s`. Then, iterate through the string `t`, and for each character, find its original index from the map and calculate the absolute difference with its current index in `t`. Summing up these differences gives the final result. This two-pass approach is optimal.

---

## 🧮 Complexity Analysis
- Time: O(N), where N is the length of the strings. We iterate through both strings once.  
- Space: O(K), where K is the number of unique characters. In the worst case, this is O(N).

---

## 📖 Notes
- **Real-world analogy:** Imagine you're organizing a race. At the starting line, each runner is given a bib number which is their starting position (`s`). You quickly jot down a list: Runner 'A' is in position 0, Runner 'B' is in position 1, etc. This list is your hash map. After the race, the runners finish in a different order (`t`). To calculate a "shuffling score," you go through the finishing line order. For each runner, you look at their finishing position, check your list for their *original* starting position, and find the difference. The total score is the sum of all these differences.
- **Edge cases considered:** The problem statement guarantees the strings are permutations, so we don't need to handle missing characters.
