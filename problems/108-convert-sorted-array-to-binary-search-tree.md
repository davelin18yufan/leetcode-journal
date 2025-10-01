# 108. Convert Sorted Array to Binary Search Tree

**Difficulty:** Easy
**Algorithm:** Divide and Conquer
**Data Structure:** Array, Tree, Binary Search Tree
**Date:** 2025-10-01

---

## 📝 Problem Description

The goal is to convert a given integer array `nums`, which is sorted in ascending order, into a **height-balanced** binary search tree.

---

## Real-world analogy

This problem is exactly like creating a **fair tournament bracket** for a competition where players are ranked (seeded) from best to worst. The `nums` array is your list of ranked players.

To make the bracket as balanced as possible, you don't have the #1 and #2 seeds play each other right away. Instead, you:

1.  **Pick the player in the exact middle** of the ranking. They are the "final boss" and will be the **root** of your tournament tree.
2.  All the players in the **first half** of the list (those with better rankings) are put into the **left side of the bracket**.
3.  All the players in the **second half** of the list are put into the **right side of the bracket**.
4.  You then apply the **exact same logic recursively** to build the left and right brackets until all players have a spot.

---

## 💡 Key Idea

The core idea is to use a recursive "divide and conquer" approach. To ensure the tree is height-balanced, we must always pick the **middle element** of the current array segment to be the root of the (sub)tree. The left half of the segment forms the left subtree, and the right half forms the right subtree. This process is repeated until all elements are placed in the tree.

---

## 🧮 Complexity Analysis

- **Time:** `O(N)`, where N is the number of elements in the array. Each element is visited once to be created as a tree node.
- **Space:** `O(log N)`, which is the height of the tree, used by the recursion stack. This is the optimized space complexity that avoids slicing the array.

---

## 📖 Notes
- **Status:** 🚧 WIP (Work In Progress). This file contains the analysis and solution approach but is pending final review.
- **Optimization:** The most optimal solution uses left and right pointers to define the subarray, avoiding the `O(N)` cost of slicing the array in each recursive call.
- **Edge cases:** An empty input array should result in a `null` tree.
