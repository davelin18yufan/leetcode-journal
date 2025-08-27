# 3407. Substring Matching Pattern

**Difficulty:** Medium
**Algorithm:** String Manipulation
**Data Structure:** String
**Date:** 2025-08-27

---

## 📝 Problem Description
Given two strings, `s` (the text) and `p` (the pattern), where `p` contains exactly one wildcard character `*`, determine if `p` matches `s`. The `*` can match any sequence of characters (including an empty sequence).

---

## 💡 Key Idea
The core idea is to split the pattern `p` into a `prefix` and a `suffix` using the `*` as a delimiter. The problem then simplifies to checking if `s` starts with the `prefix` and ends with the `suffix`, with the correct ordering.

To make the check robust, we find the *first* occurrence of the `prefix` and the *last* occurrence of the `suffix`. A match is valid if both are found and the prefix's ending position is less than or equal to the suffix's starting position.

---

## 🧮 Complexity Analysis
- Time: O(S * P), where S and P are the lengths of the strings, due to the nature of built-in substring search functions like `indexOf` and `lastIndexOf`.
- Space: O(P) to store the `prefix` and `suffix`.

---

## 📖 Notes
- Real-world analogy: A wildcard file search, like `report_*.docx`, where `*` can be anything.
- Using `lastIndexOf` for the suffix is a key trick, as it maximizes the space available for the `*` wildcard, correctly handling cases like `s = "banana", p = "b*a"`.
- Edge cases: The `*` is at the beginning or end of the pattern, resulting in an empty prefix or suffix.
