# 111. Minimum Depth of Binary Tree

**Difficulty:** Easy
**Algorithm:** Breadth-First Search, Depth-First Search
**Data Structure:** Tree, Binary Tree
**Date:** 2025-10-03

---

## 📝 Problem Description
Given a binary tree, find its minimum depth. The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node. A leaf is a node with no children.

---

## Real-world analogy
Imagine you're standing on the top floor of a large building with many branching staircases, and you need to find the **shortest path to a fire escape**. A fire escape is a "leaf node" – a room with no further doors. BFS is like sending explorers down every staircase simultaneously, level by level. The first explorer to find a fire escape has found the shortest path, and the search can stop immediately.

---

## 💡 Key Idea
For any "shortest path" problem on a tree or graph, Breadth-First Search (BFS) is the optimal strategy. Because it explores level by level, the **first leaf it finds is guaranteed to be the nearest one**. This means we can stop searching and return the current depth as soon as we encounter a node with no children.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the number of nodes. In the best case (root is a leaf), it's O(1). In the worst case (a skewed tree), we visit all nodes.
- Space: `O(W)`, where W is the maximum width of the tree. This is for the queue used in BFS.

---

## 📖 Notes
- Real-world analogy: Finding the shortest path to a fire escape in a building.
- Edge cases considered: empty tree (depth 0), root node being a leaf (depth 1).
- BFS is more efficient than DFS for this problem because DFS might explore a very deep branch completely before finding a much shorter path on another branch.
