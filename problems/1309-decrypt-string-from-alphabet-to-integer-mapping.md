# 1309. Decrypt String from Alphabet to Integer Mapping

**Difficulty:** Easy  
**Algorithm:** String Manipulation, Iteration  
**Data Structure:** String  
**Date:** 2025-10-22  

---

## 📝 Problem Description
Decrypt a string where digits '1'-'9' map to 'a'-'i' and '10#'-'26#' map to 'j'-'z'.

---

## Real-world analogy
Think of this like translating Morse code, but with two different dot/dash patterns. Short patterns (1 to 9) mean one thing, and longer patterns (10# to 26#) mean another. Your code is like having a lookup book, but you only wrote down the short patterns. When you see a long pattern, you try to look up part of it, which doesn't work. The better way is to just know the rules directly.

---

## 💡 Key Idea
Iterate through the string from left to right. If a '#' is encountered two positions ahead, it signifies a two-digit number. Otherwise, it's a single-digit number. Convert the number to its corresponding character using ASCII values.

---

## 🧮 Complexity Analysis
- Time: `O(N)` 
- Space: `O(N)`

---

## 📖 Notes
- Real-world analogy: Translating Morse code with varying patterns for single and double-digit representations.
- Edge cases considered: empty string, single-digit numbers, two-digit numbers with '#'.