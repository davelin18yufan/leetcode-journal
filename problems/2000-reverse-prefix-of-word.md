# 2000. Reverse Prefix of Word

**Difficulty:** Easy  
**Algorithm:** Two Pointers, String  
**Data Structure:** String  
**Date:** 2025-10-31  

---

## 📝 Problem Description
Given a 0-indexed string `word` and a character `ch`, reverse the segment of `word` that starts at index 0 and ends at the index of the first occurrence of `ch` (inclusive). If the character `ch` does not exist in `word`, do nothing.

---

## Real-world analogy
This problem is like finding the first "stop" sign (`ch`) on a long road (`word`). When you find it, you take the entire section of road from the beginning to that stop sign, reverse its direction, and then reconnect it to the rest of the road. If you never find a "stop" sign, you just leave the whole road as-is.

---

## 💡 Key Idea
The main idea is to find the index of the first occurrence of the character `ch`. If it's found, we split the string into two parts: the prefix (from the start to `ch`) and the suffix (the rest of the string). We then reverse the prefix and concatenate it back with the suffix.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the length of the word. This is because finding the character, slicing the string, and reversing the prefix all take linear time.
- Space: `O(N)` to store the new reversed prefix and the final resulting string, as strings are immutable in many languages.

---

## 📖 Notes
- Real-world analogy: Reversing a segment of a road up to a specific landmark.
- A simple and effective approach is to use built-in functions to find the character's index and slice the string. The reversal can be done manually with a loop or with built-in methods.
