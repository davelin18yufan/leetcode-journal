# 459. Repeated Substring Pattern

**Difficulty:** Easy  
**Algorithm:** String Matching  
**Data Structure:** String  
**Date:** 2025-10-07  

---

## 📝 Problem Description
Given a string, check if it can be constructed by taking a substring of it and appending multiple copies of the substring together.

---

## Real-world analogy
This problem is like checking for a repeating wallpaper pattern. You have a long strip of wallpaper (`s`). You want to know if the entire strip is just a smaller, single pattern repeated over and over. The approach is to take a small piece from the beginning, see if repeating it covers the whole strip, and if not, try a slightly larger piece, continuing until a match is found or all possibilities are exhausted.

---

## 💡 Key Idea
The core insight is that if a string `s` is formed by a repeating substring, then concatenating `s` with itself (`s + s`) will create a new string that must contain the original `s` within its "middle" part (i.e., excluding the very first and very last characters).

---

## 🧮 Complexity Analysis
- Time: `O(N)` 
- Space: `O(N)`

---

## 📖 Notes
- Real-world analogy: Verifying a repeating wallpaper pattern.
- Key insight: A string `s` made of a repeating pattern will always be found inside the string `(s + s).substring(1, s.length * 2 - 1)`.
