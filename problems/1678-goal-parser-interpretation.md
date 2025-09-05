# 1678. Goal Parser Interpretation

**Difficulty:** Easy  
**Algorithm:** String Manipulation  
**Data Structure:** String  
**Date:** 2025-09-05  

---

## 📝 Problem Description
The problem requires interpreting a string command where "G" maps to "G", "()" maps to "o", and "(al)" maps to "al". The goal is to concatenate these interpretations into a final string.

---

## 💡 Key Idea
The core idea is to process the input string from left to right. When a 'G' is encountered, it's appended directly. When a '(' is found, we must look ahead at the next character. If it's a ')', we append 'o'; otherwise, it must be the "(al)" sequence, so we append "al". An even simpler approach is to use built-in string replacement functions to substitute "()" with "o" and "(al)" with "al".

---

## 🧮 Complexity Analysis
- **Time:** O(N), where N is the length of the input string, because we must scan the entire string once.
- **Space:** O(N), as the output string can have a length proportional to the input string in the worst case.

---

## 📖 Notes
- **Real-world analogy:** This is similar to a telegraph operator decoding a simplified Morse Code. A 'G' is a simple signal. A '(' is a signal to check the next character to differentiate between a short sequence `()` and a longer one `(al)`, much like a telegrapher distinguishes between different dot-dash combinations that start similarly.
- **Edge cases:** An empty input string should produce an empty output string. The solution should handle inputs containing only one type of token (e.g., all "G"s or all "()").
