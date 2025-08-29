# 387. First Unique Character in a String

**Difficulty:** Easy
**Algorithm:** Two-Pass Hash Map
**Data Structure:** Hash Table
**Date:** 2025-08-29

---

## 📝 Problem Description

Given a string `s`, find the first non-repeating character in it and return its index. If a unique character does not exist, return -1.

---

## 💡 Key Idea

The problem can be solved efficiently using a two-pass approach with a hash map.

1.  **First Pass (Build Frequency Map):** Iterate through the string once to build a frequency counter that maps each character to its number of occurrences.
2.  **Second Pass (Find First Unique):** Iterate through the string a second time. For each character, check its count in the frequency map. The first character encountered with a count of `1` is the answer. Return its index immediately.

If the second loop completes without finding a unique character, it means none exists, and we return -1. This method cleanly separates the "counting" and "finding" logic.

---

## 🧮 Complexity Analysis

- **Time Complexity:** O(N), where N is the length of the string. We iterate through the string a constant number of times (twice).
- **Space Complexity:** O(1), because the problem is constrained to lowercase English letters (a-z), the hash map will store at most 26 key-value pairs, which is constant space.

---

## 📖 Notes

- **Real-world Analogy:** Imagine a teacher finding the first student on the roster who submitted a unique project idea. First, they tally up how many times each idea appears. Then, they go down the original roster, and the first student whose project idea has a tally of one is the winner.
- **Edge Cases:**
    - An empty string (`s = ""`) should return -1.
    - A string with no unique characters (`s = "aabbcc"`) should return -1.
    - A string where all characters are unique (`s = "abcde"`) should return 0.
