# 2710. Remove Trailing Zeros From a String

**Difficulty:** Easy
**Algorithm:** String Manipulation
**Data Structure:** String
**Date:** 2025-12-08

---

## 📝 Problem Description
Given a string `num` representing a positive integer, the task is to remove all trailing zeros from it.

---

## Real-world analogy
Imagine you have a piece of thread, and some of it is frayed at the end. You want to trim off the frayed parts (the zeros) to get to the solid part of the thread (the non-zero digit). You would start cutting from the very end, and you'd keep snipping off bits until you hit the main, solid thread. You wouldn't start from the middle, because the beginning and middle are fine. This process of trimming from the end is exactly like removing trailing zeros from a number string.

---

## 💡 Key Idea
The core idea is to find the last character that is not a '0'. All characters from the beginning of the string up to and including that character will form the new string. We can achieve this by iterating backward from the end of the string and stopping at the first non-zero character encountered.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the length of the string. In the worst-case scenario, we might have to traverse a significant portion of the string.
- Space: `O(N)`, as a new string is created for the result. In some languages, if the string is mutable and slicing is cheap, it could be O(1), but in JavaScript/TypeScript, `substring` creates a new string.

---

## 📖 Notes
- Real-world analogy: This is similar to trimming trailing whitespace from user input fields to sanitize the data before processing or storing it.
- Edge cases: A string with no trailing zeros (e.g., "123") should be returned as is. The problem statement guarantees a positive integer, so we don't need to worry about a string of all zeros or an empty string.
