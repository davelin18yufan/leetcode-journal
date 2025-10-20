# 3355. Zero Array Transformation I

**Difficulty:** Medium  
**Algorithm:** Prefix Sum  
**Data Structure:** Array  
**Date:** 2025-10-20  

---

## 📝 Problem Description
Given an array of integers `nums` and a set of queries, where each query is a range `[l, r]`, we can decrement the values in `nums` within that range. The problem is to determine if it's possible to make all elements in `nums` zero by applying these operations. Each query can be used multiple times.

---

## Real-world analogy
Imagine you have a long street (`nums`) and several city workers (`queries`) who are assigned sections of the street to sweep. Each worker sweeps their assigned section `[l, r]` exactly once. You want to know the *total number of times each block of the street was swept*.

  * **Your Current Approaches (Inefficient):**

      * Method 1: Get the list of all workers. For each worker, walk their assigned section and make a tally mark for each block they sweep.
      * Method 2: Go to the first block of the street. Ask every single worker if they swept this block. Repeat for every block.
        Both involve a lot of repetitive checking.

  * **The Difference Array Approach (Efficient):**

    1.  Get a blank map of the street (`difference` array, size N+1, all zeros).
    2.  For each worker assigned section `[l, r]`:
          * Go to the *start* block `l` and put a `+1` sign (meaning "sweeping starts here").
          * Go to the block *just after the end* (`r + 1`) and put a `-1` sign (meaning "sweeping stops just before here").
    3.  Now, walk down the street once, keeping a running total (`currentSweeps`).
          * Start with `currentSweeps = 0`.
          * When you reach block `i`, look at the sign you placed: `currentSweeps += sign_at_block_i`.
          * The value of `currentSweeps` at block `i` is the total number of times block `i` was swept!

---

## 💡 Key Idea
The core idea is to determine, for each index `i`, the total number of times it can be decremented. This is the number of queries `[l, r]` such that `l <= i <= r`. If for any `i`, `nums[i]` is greater than the number of times it can be decremented, then it's impossible to make it zero.

A naive approach of checking each query for each index would be too slow (O(N*Q)). A much more efficient approach is to use a **difference array** (or prefix sum). We can create an array `diff` of size `n+1`. For each query `[l, r]`, we increment `diff[l]` and decrement `diff[r+1]`. After processing all queries, we can compute the prefix sum of `diff`. The value of the prefix sum at index `i` will give us the total number of times `nums[i]` can be decremented.

---

## 🧮 Complexity Analysis
- Time: `O(N + Q)` where N is the length of `nums` and Q is the number of queries.
- Space: `O(N)` for the difference array.

---

## 📖 Notes
- Real-world analogy: Calculating the total coverage of multiple overlapping intervals, like the number of times a street block is swept by different cleaning crews.
- Edge cases considered: queries that go to the end of the array.
