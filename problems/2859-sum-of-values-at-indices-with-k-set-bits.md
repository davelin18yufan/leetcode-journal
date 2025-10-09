# 2859. Sum of Values at Indices With K Set Bits

**Difficulty:** Easy  
**Algorithm:** Bit Manipulation  
**Data Structure:** Array  
**Date:** 2025-10-09  

---

## 📝 Problem Description
Given a 0-indexed integer array `nums` and an integer `k`, the task is to find the sum of all `nums[i]` where the number of set bits (1s) in the binary representation of the index `i` is exactly `k`.

---

## Real-world analogy
This problem is like being a quality control inspector in a warehouse.

  * The `nums` array represents items on a series of shelves.
  * The shelf number is the `index`.
  * Each shelf number has a special "digital barcode" which is its binary representation.
  * Your boss gives you a rule (`k`): "I only want the items from shelves where the barcode has **exactly `k` active lights** (set bits)."

Your job is to go to each shelf, check its barcode's light count, and if it matches the rule, you take the item and add it to your total collection. This process directly simulates the algorithm.

---

## 💡 Key Idea
The core task is to efficiently count the number of set bits for each index `i`. Instead of converting the index to a string (`i.toString(2)`) and iterating, a more performant approach is to use bit manipulation. Brian Kernighan's algorithm is particularly elegant: the operation `n & (n - 1)` clears the least significant set bit. By repeatedly applying this operation in a loop until the number becomes zero, the number of iterations gives the exact count of set bits.

---

## 🧮 Complexity Analysis
- Time: `O(N * log M)`, where N is the length of `nums` and M is the maximum value of an index. The `log M` factor comes from the number of bits in the index.
- Space: `O(1)` (when using bit manipulation, as no extra space is needed for string conversion).

---

## 📖 Notes
- Real-world analogy: A warehouse inspector selecting items from shelves based on a "digital barcode" rule (the number of set bits in the shelf's index).
- Edge cases considered: `k` being 0 (only index 0 qualifies), `k` being larger than the number of bits in any possible index.
