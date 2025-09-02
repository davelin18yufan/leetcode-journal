# 2269. Find the K-Beauty of a Number

**Difficulty:** Easy
**Algorithm:** Sliding Window
**Data Structure:** String
**Date:** 2025-09-02

---

## 📝 Problem Description
The k-beauty of an integer `num` is defined as the number of its substrings (of length `k`) that are divisors of `num`. The task is to find this value. For example, if `num = 240` and `k = 2`, the substrings are "24" and "40". Since 240 is divisible by 24, but not 40, the k-beauty is 1.

---

## 💡 Key Idea
The core idea is to use a **sliding window** approach. We convert the number to a string to easily access its digits. Then, we iterate through the string, creating a "window" of `k` characters at a time. For each substring (window), we convert it back to a number and check if it divides the original number `num`. We must also handle the edge case where the substring represents the number 0, as division by zero is not allowed.

---

## 🧮 Complexity Analysis
- **Time:** O(L), where L is the number of digits in `num`. We perform a single pass through the digits.
- **Space:** O(1). The space used for the substring is constant since `k` is small and bounded.

---

## 📖 Notes
- **Real-world analogy:** Imagine you're a data analyst looking at a long string of stock price digits, say `430043`. Your manager asks you to find a special "2-hour pattern" (`k=2`). A pattern is "special" if the original 6-hour price (`430043`) is perfectly divisible by the price from that 2-hour window. You would use a "sliding window" of 2 hours, check for divisibility (`430043 % 43 == 0`), and slide the window across the entire string of digits (`"30"`, `"00"`, `"04"`, `"43"`) to count all such special patterns.
- **Edge cases considered:** Substrings that form the number 0 (which cannot be a divisor), and ensuring the sliding window does not go out of bounds.
