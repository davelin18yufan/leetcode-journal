# 125. Valid Palindrome

**Difficulty:** Easy
**Algorithm:** Two Pointers
**Data Structure:** String
**Date:** 2025-12-22

---

## 📝 Problem Description
Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

---

## Real-world analogy
In bioinformatics, scientists often search for palindromic sequences in DNA. These sequences, which read the same forwards and backwards (considering the complementary strand), are often recognition sites for restriction enzymes. An algorithm must be able to identify these sequences even with noise or formatting symbols in the raw data, ignoring non-essential information to determine if the sequence is symmetrical. This is crucial for detecting genetic mutations or understanding protein synthesis.

---

## 💡 Key Idea
Use a two-pointer approach. Start one pointer at the beginning of the string and another at the end. Move them towards each other, skipping any non-alphanumeric characters. At each step, compare the characters (ignoring case). If a mismatch is found, the string is not a palindrome. If the pointers cross, the string is a palindrome.

---

## 🧮 Complexity Analysis
- Time: `O(N)`
- Space: `O(1)` (when using the in-place two-pointer method)

---

## 📖 Notes
- Real-world analogy: Checking for palindromic DNA sequences in bioinformatics.
- Edge cases considered: empty string, strings with only non-alphanumeric characters, case differences.
