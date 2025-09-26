# 724. Find Pivot Index

**Difficulty:** Easy  
**Algorithm:** Prefix Sum  
**Data Structure:** Array  
**Date:** 2025-09-26  

---

## 📝 Problem Description
Given an array of integers `nums`, calculate the pivot index of this array. The pivot index is the index where the sum of all the numbers strictly to the left of the index is equal to the sum of all the numbers strictly to the index's right. If the index is on the left edge of the array, then the left sum is 0 because there are no elements to the left. This also applies to the right edge of the array. Return the leftmost pivot index. If no such index exists, return -1.

---

## Real-world analogy
Imagine you have a long board with different weights placed on it (the `nums` array). Your job is to find the exact spot to place a fulcrum to make the board **perfectly balanced**. The "Prefix Sum" approach is a smart way to do this. First, you get the **total weight** of the entire board. Then, you start with the fulcrum at the far left and slide it to the right, one spot at a time. At each spot, you don't need to re-weigh both sides. Instead, you just update the sums: the `leftSum` increases by the weight you just passed, and the `rightSum` decreases by the weight you're now on. This way, you can efficiently find the balance point in a single pass.

---

## 💡 Key Idea
The core idea is to use the "Prefix Sum" technique to avoid recalculating sums repeatedly. By first computing the `totalSum` of the array, we can find the `rightSum` at any index `i` in O(1) time by using the formula: `rightSum = totalSum - leftSum - nums[i]`. We iterate through the array once, maintaining a `leftSum`, and check for the balance condition at each index.

---

## 🧮 Complexity Analysis
- Time: `O(N)` 
- Space: `O(1)`

---

## 📖 Notes
- Real-world analogy: Balancing a seesaw or finding the center of mass.
- Edge cases considered: empty array, array with one element, no pivot index found.
