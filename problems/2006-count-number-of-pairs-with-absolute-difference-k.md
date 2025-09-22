# 2006. Count Number of Pairs With Absolute Difference K

**Difficulty:** Easy  
**Algorithm:** Hash Table, Counting  
**Data Structure:** Array, Hash Table  
**Date:** 2025-09-22  

---

## 📝 Problem Description
Given an integer array `nums` and an integer `k`, the task is to find the number of pairs `(i, j)` where `i < j` and the absolute difference between the elements `|nums[i] - nums[j]|` is equal to `k`.

---

## Real-world analogy
Imagine you're a party planner trying to find pairs of guests whose age difference is exactly `k` years. Instead of asking every single guest their age and comparing them to everyone else (a slow O(N²) process), you can be more efficient. You can stand by the door with a clipboard (a hash map). As each guest arrives, you jot down their age. For every new guest, you just glance at your clipboard to see if someone with the required age (`age - k` or `age + k`) has already arrived. This way, you only check each guest once, making it a much faster O(N) operation.

---

## 💡 Key Idea
The most efficient way to solve this is by using a hash map to keep track of the numbers we have seen and their frequencies. We iterate through the array a single time. For each number `num`, we check if its potential partners (`num - k` or `num + k`) are already in our hash map. If they are, we add their stored frequencies to our total pair count. After checking, we update the map with the current number, making it available for subsequent elements.

---

## 🧮 Complexity Analysis
- **Time:** `O(N)`, where N is the number of elements in the array. We only need a single pass.
- **Space:** `O(U)`, where U is the number of unique elements in the array. In the worst case, this is `O(N)`.

---

## 📖 Notes
- This problem is a classic example of trading space for time. The hash map uses extra space to achieve a linear time complexity, which is a significant improvement over the O(N²) brute-force approach.
- The real-world analogy highlights how using a hash map for quick lookups is similar to checking a pre-compiled list instead of re-scanning everything.
