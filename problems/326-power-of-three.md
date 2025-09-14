# 326. Power of Three

**Difficulty:** Easy
**Algorithm:** Math
**Data Structure:** N/A
**Date:** 2025-09-14

---

## 📝 Problem Description
The problem asks us to determine if a given integer `n` is a power of three. An integer `n` is a power of three if there exists an integer `x` such that `n == 3^x`.

---

## 💡 Key Idea
The most efficient and robust solution avoids loops, recursion, and floating-point math by using an integer limitation trick.

The problem constraints state that `n` is a 32-bit signed integer. The largest power of 3 that fits within this range is `3^19 = 1162261467`. Any number `n` that is a power of three (e.g., `3^2`, `3^5`) must be a divisor of this largest possible power of three.

Therefore, the algorithm is simple: check if `n` is positive and if `1162261467` is perfectly divisible by `n`.

---

## 🧮 Complexity Analysis
- **Time:** O(1) - The check is a single arithmetic operation.
- **Space:** O(1) - No extra space is used that scales with the input.

---

## 📖 Notes
- **Real-world analogy:** Think of checking if a set of **Russian Nesting Dolls** is a "perfect power-of-three set." A set is perfect if every doll is exactly 3 times smaller than the one that contains it, and the innermost doll has a size of 1. Our algorithm is like having the largest possible "perfect" doll and checking if our given doll `n` is one of the dolls that belongs in that master set.
- **Edge cases considered:** The primary edge case is any non-positive number (`n <= 0`), which can never be a power of three. The check `n > 0` handles this.
