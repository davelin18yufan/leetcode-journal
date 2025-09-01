# 3110. Score of a String

**Difficulty:** Easy
**Algorithm:** String Manipulation
**Data Structure:** String
**Date:** 2025-09-01

---

## 📝 Problem Description
Calculates the "score" of a string, defined as the sum of the absolute differences between the ASCII values of all adjacent characters.

---

## 💡 Key Idea
The core idea is to perform a single pass through the string, from the first character up to the second-to-last. In each step, we find the ASCII values of the current character and the one immediately following it, compute their absolute difference, and add it to a running total. This avoids any complex data structures or multiple passes, making it highly efficient.

---

## 🧮 Complexity Analysis
- Time: O(N), where N is the length of the string, as we must visit each character once.
- Space: O(1), as we only use a few variables to store the running score and loop index.

---

## 📖 Notes
- **Real-world analogy**: This is like calculating the **total elevation change on a hike**. Each character's ASCII value is a point's height, and the score is the total climb and descent. For `s = "hello"`, the heights are `[104, 101, 108, 108, 111]`. The total change is `|104-101| + |101-108| + |108-108| + |108-111| = 3 + 7 + 0 + 3 = 13`.
- **Edge cases**: The loop condition `i < s.length - 1` correctly handles edge cases like an empty or single-character string (the loop won't run) and prevents an out-of-bounds error.
