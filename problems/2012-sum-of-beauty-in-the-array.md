# 2012. Sum of Beauty in the Array

**Difficulty:** Medium  
**Algorithm:** Prefix Sum, Array  
**Data Structure:** Array  
**Date:** 2025-10-16  

---

## 📝 Problem Description
You are given a 0-indexed integer array `nums`. For each index `i` in the range `1` to `n-2`, you need to calculate its "beauty" based on its neighbors and the rest of the array. The total beauty is the sum of the beauty of all such indices.

---

## Real-world analogy
Imagine the `nums` array represents a **mountain range**. You are standing at a point `nums[i]`.

- **Beauty of 2:** This is a very special peak. To get a score of 2, you must be **strictly higher than every single point to your left** AND **strictly lower than every single point to your right**. You are the highest point of the entire western range and the lowest point of the entire eastern range.
- **Beauty of 1:** This is just a small, local peak. You are strictly higher than your **immediate neighbors** (`nums[i-1]` and `nums[i+1]`), but you might not be the highest in the whole western range or lowest in the whole eastern range.
- **Beauty of 0:** This is a valley or a flat plateau.

The goal is to calculate the total beauty score by examining each eligible peak in the mountain range.

---

## 💡 Key Idea
The core of the problem is to efficiently check the two conditions for beauty. A brute-force check for the "beauty of 2" condition (checking all elements to the left and right for every `i`) would be too slow (O(N²)).

The optimal strategy is to use a **preprocessing** technique. We can pre-calculate the maximum value for all prefixes and the minimum value for all suffixes of the array.

1.  **`prefixMax` array:** `prefixMax[i]` stores the maximum value in `nums[0...i]`.
2.  **`suffixMin` array:** `suffixMin[i]` stores the minimum value in `nums[i...n-1]`.

With these two arrays, checking if `nums[i]` is greater than all elements to its left (`prefixMax[i-1]`) and smaller than all elements to its right (`suffixMin[i+1]`) becomes an O(1) operation.

---

## 🧮 Complexity Analysis
- Time: `O(N)` for three passes (prefix max, suffix min, final beauty calculation).
- Space: `O(N)` to store the prefix and suffix arrays.

---

## 📖 Notes
- This problem is a classic example of trading space for time. By using extra arrays for preprocessing, we reduce the time complexity from O(N²) to O(N).
- Marked as **incomplete** for future review and to complete the implementation details.
