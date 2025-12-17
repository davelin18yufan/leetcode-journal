# 20. Valid Parentheses

**Difficulty:** Easy  
**Algorithm:** Stack  
**Data Structure:** Stack  
**Date:** 2025-12-17  

---

## 📝 Problem Description
The problem requires us to determine if an input string containing just the characters '(', ')', '{', '}', '[' and ']' is valid. A string is valid if open brackets are closed by the same type of brackets and in the correct order.

---

## Real-world analogy
This logic is fundamental in software development, particularly for compilers and code editors. When you write code, the editor or compiler checks for syntax errors, such as a missing closing brace `}`. It parses the code as a stream of characters and uses a stack to ensure that all brackets like `{}`, `()`, and `[]` are properly paired and nested. An imbalance will trigger a syntax error, preventing the code from compiling or highlighting the issue in the editor.

---

## 💡 Key Idea
The core insight is to use a Stack, which follows a Last-In-First-Out (LIFO) principle. We iterate through the string:
1. If we encounter an opening bracket, we push its corresponding closing bracket onto the stack.
2. If we see a closing bracket, it must match the bracket at the top of the stack. If it does, we pop the stack. If it doesn't, or if the stack is empty, the string is invalid.
Finally, a valid string will result in an empty stack at the end.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the length of the string, as we traverse it once.
- Space: `O(N)` in the worst-case scenario where the string consists of all opening brackets.

---

## 📖 Notes
- Real-world analogy: Checking for balanced brackets in a code editor or parsing HTML/XML tags.  
- Edge cases to consider include an empty string (which is valid), a string with an odd number of characters, and strings where closing brackets don't match the last opening one.
