# 2255. Count Prefixes of a Given String

**Difficulty:** Easy
**Algorithm:** String Manipulation
**Data Structure:** Array, String
**Date:** 2025-09-10

---

## 📝 Problem Description
Given an array of strings `words` and a string `s`, the task is to count how many of the strings in the `words` array are prefixes of `s`. A string is considered a prefix if it appears at the very beginning of another string.

---

## 💡 Key Idea
The main insight is to iterate through each `word` in the `words` array and check if the main string `s` starts with that `word`. The most direct and readable way to implement this check in JavaScript/TypeScript is by using the built-in `s.startsWith(word)` method.

---

## 🧮 Complexity Analysis
- **Time:** O(N * M), where N is the number of items in the `words` array and M is the average length of a word. This is because for each of the N words, the `startsWith` check can take up to M character comparisons in the worst case.
- **Space:** O(1), as the solution uses a constant amount of extra space (for the counter) regardless of the input size.

---

## 📖 Notes
- **Real-world analogy:** This mechanism is exactly like an **autocomplete feature** in a search bar or code editor. The system checks its dictionary (`words`) to see how many suggestions are valid prefixes of what the user is currently typing (`s`).
- **Alternative Implementation:** An alternative to `s.startsWith(w)` is `s.indexOf(w) === 0`, which achieves the same result. However, `startsWith` is generally preferred for its clear, semantic meaning.
- **Optimization for multiple queries:** While the current approach is optimal for a single run, if this function were to be called repeatedly with a massive `words` dictionary, pre-processing the words into a **Trie (Prefix Tree)** would be a more efficient strategy for the long run.
