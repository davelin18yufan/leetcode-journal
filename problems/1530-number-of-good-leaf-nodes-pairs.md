# 1530. Number of Good Leaf Nodes Pairs

**Difficulty:** Medium  
**Algorithm:** Depth-First Search  
**Data Structure:** Tree  
**Date:** 2025-10-19  

---

## 📝 Problem Description

Given the root of a binary tree and an integer `distance`, a pair of two different leaf nodes of this tree is said to be **good** if the length of the shortest path between them is less than or equal to `distance`. This file records the process of solving this problem, noting that the initial approach was flawed and the final solution uses a post-order DFS.

---

## Real-world analogy

Imagine a company's organizational chart as a tree. The "leaf nodes" are employees who don't manage anyone. The `distance` is a "communication limit." A pair of employees is considered "good" if the communication path between them is within this limit. The path is measured by going up from one employee to their closest common manager (the Lowest Common Ancestor or LCA) and then down to the other employee.

For example, two employees in the same department have their direct manager as their LCA, resulting in a short path. Employees in different divisions might have the CEO as their LCA, leading to a much longer path. The goal is to count all pairs of employees who can communicate efficiently within the given distance limit.

---

## 💡 Key Idea

The optimal strategy is to use a **post-order Depth-First Search (DFS)**. A recursive function traverses the tree from the bottom up. At each node, this function performs two main tasks:

1.  **Calculate Good Pairs:** It receives lists of distances from its left and right children to their respective leaf nodes. The current node acts as the Lowest Common Ancestor (LCA) for leaves in its left and right subtrees. It iterates through all pairs of left/right distances, and if their sum is less than or equal to the `distance`, it increments a total counter.
2.  **Return Distances to Parent:** It gathers all the leaf distances from its children, increments them by one (to account for the path to the parent), and returns this new list of distances to its parent node. This allows higher-level nodes to perform the same calculation.

---

## 🧮 Complexity Analysis

- Time: `O(N * D^2)`, where N is the number of nodes and D is the `distance`. In the worst-case scenario, the lists of distances passed up the tree can grow, leading to a quadratic number of comparisons at each node.
- Space: `O(N * D)` in the worst case, for the recursion stack and the arrays of distances being passed up.

---

## 📖 Notes
- **Status:** Marked for review as requested. The solution is based on a post-order DFS strategy which correctly handles the Lowest Common Ancestor (LCA) logic.
- The initial BFS approach was flawed because it only considered the root as the LCA and used node values instead of path distances.
- The key insight is that each node can act as an LCA for the leaves in its subtrees.
