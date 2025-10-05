# 941. Valid Mountain Array

**Difficulty:** Easy  
**Algorithm:** Two Pointers, Array Traversal  
**Data Structure:** Array  
**Date:** 2025-10-05  

---

## 📝 Problem Description
Given an array of integers `arr`, return `true` if and only if it is a valid mountain array. An array is a mountain array if and only if:
1. `arr.length >= 3`
2. There exists some `i` with `0 < i < arr.length - 1` such that:
   - `arr[0] < arr[1] < ... < arr[i-1] < arr[i]`
   - `arr[i] > arr[i+1] > ... > arr[arr.length - 1]`

---

## Real-world analogy
Think of this problem as verifying a **hike up and down a single mountain peak**. The `arr` represents the elevation at each step of your hike. For it to be a valid "mountain hike," you must:

1.  **Start by walking strictly uphill.** You cannot go flat or downhill at the start.
2.  **Reach a single peak.** You cannot still be climbing when you reach the end of the trail, nor can the trail start at the peak.
3.  **From the peak, walk strictly downhill** all the way to the end. You cannot go flat or start climbing again.

Instead of trying to find the peak first with a complex search, we just simulate this hike from start to finish.

---

## 💡 Key Idea
The most intuitive and efficient method is to simulate the "hike" using a single pass with a pointer.

1.  **Walk Uphill:** Start a pointer `i` from the beginning and advance it as long as the elevation is strictly increasing (`arr[i] < arr[i+1]`).
2.  **Check the Peak:** After the uphill walk, the pointer `i` is at the peak. A valid peak cannot be the first or the last element of the array. If it is, the path was either all downhill or all uphill, which is not a mountain.
3.  **Walk Downhill:** Continue advancing the same pointer `i` as long as the elevation is strictly decreasing (`arr[i] > arr[i+1]`).
4.  **Verify the End:** If the pointer `i` has successfully reached the very last index of the array, it means the entire path consisted of a valid uphill climb followed by a valid downhill descent from a single peak.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the number of elements in the array. We traverse the array at most once.
- Space: `O(1)`, as we only use a few variables to keep track of the pointer and array length.

---

## 📖 Notes
- Real-world analogy: Verifying a hike profile to ensure it goes up to a single peak and then comes down.
- Edge cases considered: Array too short, no peak (all uphill or all downhill), plateau (flat ground).
