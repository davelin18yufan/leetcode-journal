# 1838. Frequency of the Most Frequent Element

**Difficulty:** Medium  
**Algorithm:** Binary Search, Greedy, Sliding Window, Sorting, Prefix Sum  
**Data Structure:** Array  
**Date:** 2025-11-03  

---

## 📝 Problem Description
The frequency of an element is the number of times it occurs in an array. You are given an integer array nums and an integer k. In one operation, you can choose an index of nums and increment the element at that index by 1.

Return the maximum possible frequency of an element after performing at most k operations.

---

## Real-world analogy
Imagine `nums` is a set of **uneven wooden posts** in the ground, sorted by height: `[1, 4, 8, 13]`. Your goal is to make a group of them the *same height*.

  * You can only add "wood" (increment), you can't cut.
  * You have a limited supply of "wood" (`k`).

What's the best strategy? It's always to make a group equal to the **tallest post in that group**. To make `[1, 4]` the same height, you must make them both `4`.

  * The "cost" is the **empty space** you need to fill.
  * For the group `[1, 4]`: Target is 4. Cost is `(4-1) = 3`.
  * For the group `[1, 4, 8]`: Target is 8. Cost is `(8-1) + (8-4) = 7 + 4 = 11`.

The "cost" to make a window `[left...right]` all equal to `nums[right]` is:
**`Cost = (target_height * window_size) - (sum_of_current_heights)`**

This is the key. Now we can use a **Sliding Window** to solve this efficiently.

---

## 💡 Key Idea
We will slide a "window" over the sorted array and find the *longest* window that we can afford to make equal. The length of that window will be our `maxFrequency`.

1.  **Sort `nums`** (O(N log N)). This is essential.
2.  Initialize two pointers, `left = 0` and `right = 0`.
3.  Keep track of the `currentSum` of the elements inside our window.
4.  Iterate with the `right` pointer, expanding the window.
5.  Inside the loop, at each step, we have a window `[left...right]`.
      * `windowSum = nums[left] + ... + nums[right]`
      * `windowLength = right - left + 1`
      * `targetHeight = nums[right]`
6.  Calculate the `cost` to make all elements in this window equal to `targetHeight`:
      * `cost = (targetHeight * windowLength) - windowSum`
7.  **Check the cost:**
      * If `cost <= k`, the window is valid! The frequency is `windowLength`. We record this and keep expanding.
      * If `cost > k`, the window is too expensive. We must **shrink** it by moving the `left` pointer forward (and subtracting `nums[left]` from `windowSum`) until the cost is valid again.
8.  The `maxFrequency` found during this process is our answer.

---

## 🧮 Complexity Analysis
- Time: `O(N log N)` 
- Space: `O(1)`

---

## 📖 Notes
- Real-world analogy: Making a group of uneven wooden posts the same height with a limited supply of wood.
- Edge cases considered: empty array, k=0.
