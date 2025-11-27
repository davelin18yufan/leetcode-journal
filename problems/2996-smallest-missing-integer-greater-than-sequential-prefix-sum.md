# 2996. Smallest Missing Integer Greater Than Sequential Prefix Sum

**Difficulty:** Easy  
**Algorithm:** Sorting  
**Data Structure:** Hash Table  
**Date:** 2025-11-27  

---

## 📝 Problem Description
The problem asks us to first identify the longest sequential prefix in an array of numbers, starting from the very first element. A sequential prefix is a sequence like `[a, a+1, a+2, ...]`. Once this prefix is identified, we calculate its sum. Then, we must find the smallest integer that is greater than or equal to this sum and is not present in the original input array.

---

## Real-world analogy
Imagine a **domino chain reaction** starting from the very first domino.

  * The "Sequential Prefix" is how many dominoes fall down in a continuous line starting from the **first one**.
  * If there is a gap or a misalignment after the 3rd domino, the chain stops there. For instance, if the dominoes are numbered 5, 6, 7, but the next one is 9, the sequential chain stops at 7.
  * It doesn't matter if there is a perfect line of 50 dominoes set up later in the room (e.g., dominoes 20 through 69); if they aren't connected to the start, they aren't part of the "prefix" chain.
  
After the initial chain falls, their values are summed up. Let's say the sum is 18. Now, we look at all the dominoes we have (not just the ones that fell). We need to find the smallest number, starting from 18, that doesn't have a corresponding domino. If we have dominoes for 18, 19, and 20, but not 21, then 21 is our answer.

---

## 💡 Key Idea
The core logic involves two main steps. First, calculate the sum of the longest sequential prefix. This is done by iterating from the second element of the array and checking if it's exactly one greater than the preceding element. The sum accumulates as long as this condition holds true; the moment it fails, the prefix is finalized, and we stop summing. Second, once we have the prefix sum, we must find the smallest missing integer. The most efficient way to do this is to convert the input array into a `Set` for constant-time `O(1)` lookups. We then enter a loop, starting with our calculated `sum`, and check if the number exists in the `Set`. We keep incrementing the number until we find one that is not in the `Set`. This number is our result.

---

## 🧮 Complexity Analysis
- Time: `O(N)` where N is the number of elements in `nums`. The initial scan to find the prefix sum takes O(N) time. Converting the array to a Set also takes O(N). The final while-loop to find the missing integer, in the worst case, might also run multiple times, but its cost is amortized and tied to the range of numbers, which is related to N.
- Space: `O(N)` because we create a `Set` to store all the numbers from the input array for efficient lookups.

---

## 📖 Notes
- Real-world analogy: A "prefix" is like a combo streak in a game that must start from the beginning without being broken.
- Edge cases considered: An array with no sequential prefix (the prefix is just the first element), an array where the prefix sum itself is the missing number, and cases where the prefix sum and several subsequent numbers all exist in the array.
