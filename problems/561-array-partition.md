# 561. Array Partition

**Difficulty:** Easy  
**Algorithm:** Greedy, Sorting  
**Data Structure:** Array  
**Date:** 2025-09-18  

---

## 📝 Problem Description
Imagine you are a matchmaker for a dance competition with `2n` dancers, each with a different skill level (nums). You have to form n pairs. The "score" for each pair is the skill level of *the less-skilled* dancer (min(a, b)). Your goal is to form pairs in a way that the sum of all the pairs' scores is maximized.

    - A Bad Strategy: If you pair the best dancer (skill 100) with the worst dancer (skill 1), that pair's score is only 1. The amazing skill of the best dancer is completely "wasted" in terms of contributing to the sum.

    - The Optimal Strategy (Your Approach): To maximize the sum of the minimums, you want to minimize the "skill gap" in each pair. You want the stronger partner's skill to be "wasted" as little as possible. The best way to do this is to line everyone up by skill level (i.e., sort the array). Then, you pair the 1st and 2nd dancers, the 3rd and 4th, the 5th and 6th, and so on.

By pairing adjacent dancers in the sorted line, you guarantee that for every min(a, b), the value b is the smallest possible value that is still greater than or equal to a. You are minimizing the "loss" in each pair, which in turn maximizes the total sum.

---

## 💡 Key Idea
The core insight is that to maximize the sum of the minimums of each pair, we should minimize the skill gap within each pair. By sorting the array in ascending order, we can then pair adjacent elements. For any pair `(a, b)` where `a <= b`, the minimum is always `a`. Thus, the optimal strategy is to sort the array and sum up every element at an even index (0, 2, 4, ...), which represents the smaller number in each pair.

---

## 🧮 Complexity Analysis
- Time: O(N log N), dominated by the sorting algorithm.
- Space: O(log N) or O(N), depending on the space complexity of the sort implementation.

---

## 📖 Notes
- **Real-world analogy:** You are a matchmaker pairing dancers by skill. To maximize the sum of the minimum skill levels in each pair, you line them up by skill and pair the 1st with the 2nd, 3rd with 4th, and so on. This minimizes the "wasted" potential of the more skilled dancer in each pair.
- **Edge cases:** The input array is guaranteed to have an even number of elements.
