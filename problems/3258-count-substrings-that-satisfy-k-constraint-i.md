# 3258. Count Substrings That Satisfy K-Constraint I

**Difficulty:** Easy  
**Algorithm:** Sliding Window  
**Data Structure:** String  
**Date:** 2025-09-16  

---

## 📝 Problem Description
Given a binary string `s` and an integer `k`, count the number of substrings where the number of '0's is less than or equal to `k`, or the number of '1's is less than or equal to `k`.

---

## 💡 Key Idea
The problem can be solved by systematically checking every possible substring. A nested loop structure is used, where the outer loop sets the starting point of the substring and the inner loop expands the substring one character at a time. By maintaining a running count of '0's and '1's as the substring expands, we can check the k-constraint for each new substring in O(1) time. This results in an overall time complexity of O(N²), which is efficient enough for the problem's constraints.

---

## 🧮 Complexity Analysis
- Time: O(N²)  
- Space: O(1)

---

## 📖 Notes
- **Real-world analogy:** Imagine a quality control inspector at a candy factory checking a long ribbon of candy with two flavors. The rule is that any valid piece must have at most `k` of one flavor or `k` of the other. The inspector must check every possible segment that can be cut from the ribbon, starting from each possible position and extending it to all possible lengths. This mirrors the algorithm's approach of iterating through all substrings.
- **Edge cases:** Consider empty strings and strings where all characters are the same. The nested loop approach handles these correctly.
