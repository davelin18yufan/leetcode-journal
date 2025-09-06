# 3099. Harshad Number

**Difficulty:** Easy
**Algorithm:** Math
**Data Structure:** N/A
**Date:** 2025-09-06

---

## 📝 Problem Description
A Harshad number (or Niven number) is an integer that is divisible by the sum of its digits. Given an integer `x`, the task is to return the sum of its digits if `x` is a Harshad number; otherwise, return -1.

---

## 💡 Key Idea
The core idea is to first calculate the sum of the digits of the input number `x`. Then, check if `x` is divisible by this sum. If it is, the sum is the answer; otherwise, the answer is -1. The digits can be extracted either by converting the number to a string or by using mathematical operations like modulo (`%`) and division (`/`).

---

## 🧮 Complexity Analysis
- **Time:** O(log₁₀ N), where N is the value of `x`. The number of operations is proportional to the number of digits in `x`.
- **Space:** O(1), when using the mathematical approach to extract digits, as it doesn't require any extra space that scales with the input size.

---

## 📖 Notes
- **Real-world Analogy:** Think of a "Harshad Number" as a "Team Player" number. A player's jersey number is the number itself (e.g., `18`). The player's "teamwork contribution" is the sum of the digits on their jersey (e.g., `1 + 8 = 9`). A player is a true **"Team Player" (a Harshad Number)** if their jersey number is perfectly divisible by their teamwork contribution. The problem asks you to identify if the number is a "Team Player" and, if so, report its "teamwork contribution" score.
- **Edge Cases:** Single-digit numbers are always Harshad numbers, as they are divisible by themselves. The provided solution handles this with an early return.
