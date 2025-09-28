# 3370. Smallest Number With All Set Bits

**Difficulty:** Easy
**Algorithm:** Bit Manipulation
**Data Structure:** N/A
**Date:** 2025-09-28

---

## 📝 Problem Description
Given a positive integer `n`, this problem requires finding the smallest integer `x` such that `x` is greater than or equal to `n`, and the binary representation of `x` consists only of set bits (i.e., all '1's).

---

## Real-world analogy
This problem is like finding the right-sized **standard shipping box** for an item. Imagine you have an item with a "size" of `n`. You only have a specific set of standard-sized boxes, and their sizes follow a pattern: 1, 3, 7, 15, 31, and so on (these are the numbers whose binary form is all 1s). You need to find the **smallest standard box that your item will fit into** (a box of size `x >= n`). Your algorithm finds the first standard box size that is large enough.

---

## 💡 Key Idea
The core idea is to generate a sequence of numbers whose binary representations are composed entirely of ones (e.g., 1, 3, 7, 15, 31...). We start with the first number in this sequence, `1`, and iteratively generate the next until we find a candidate that is greater than or equal to the input `n`. A highly efficient way to generate the next number in the sequence is using the bitwise formula `candidate = (candidate << 1) | 1`.

---

## 🧮 Complexity Analysis
- Time: `O(log N)` - The number of iterations is proportional to the number of bits in the final answer, which is logarithmic with respect to N.
- Space: `O(1)` - The bitwise approach uses a constant amount of space.

---

## 📖 Notes
- Real-world analogy: Finding the smallest standard-sized container (box, envelope) that an item will fit into.
- The bitwise operation `(candidate << 1) | 1` is a clever and performant way to generate the sequence `1, 3, 7, 15, ...` without resorting to string or math operations.
