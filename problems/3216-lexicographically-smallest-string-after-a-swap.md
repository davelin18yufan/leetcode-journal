# 3216. Lexicographically Smallest String After a Swap

**Difficulty:** Easy  
**Algorithm:** Greedy  
**Data Structure:** String  
**Date:** 2025-10-12  

---

## 📝 Problem Description
Given a string `s` consisting of digits, you may perform at most one swap between two adjacent digits that have the same parity (both are even or both are odd). The goal is to find the lexicographically smallest string that can be obtained after performing at most one such swap.

---

## Real-world analogy
This problem is like trying to get the best possible price on an item by using a single coupon. The coupon lets you swap the price tags of two adjacent items if they're in the same category (e.g., "electronics," which corresponds to parity).

You're walking down an aisle where items are arranged in a line. To get the "lexicographically smallest" number, you want to get the smallest possible digit into the earliest possible position.

A greedy approach is best: just walk down the aisle. The **very first time** you see an item that is more expensive than the one right next to it (and they're in the same category), you use your one-time coupon to swap their tags. For example, you see a `$45` item next to a `$32` item. Swapping them makes the sequence `$32`, `$45`, which is a better "deal" at that early position. Since you only get one swap, making the earliest possible improvement guarantees the best overall outcome. You can stop right there.

---

## 💡 Key Idea
The best solution is a greedy one. Since you can only swap once, you should perform the **very first valid swap you find that makes the string smaller**. A valid and beneficial swap occurs at the first index `i` where `s[i]` and `s[i+1]` have the same parity and `s[i] > s[i+1]`. Once you perform this single swap, the resulting string is guaranteed to be the lexicographically smallest possible, and you can return it immediately.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the length of the string, because we only need to iterate through the string once.
- Space: `O(N)` to store the character array for swapping, or `O(1)` if in-place modification were allowed for strings.

---

## 📖 Notes
- Real-world analogy: Optimizing a sequence with a single, constrained, local adjustment.
- The greedy choice works because a swap at an earlier position has a greater lexicographical impact than any swap that could be made later.
