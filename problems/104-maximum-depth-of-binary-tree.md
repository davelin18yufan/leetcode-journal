# 104. Maximum Depth of Binary Tree

**Difficulty:** Easy  
**Algorithm:** Depth-First Search, Breadth-First Search  
**Data Structure:** Tree, Binary Tree  
**Date:** 2025-09-17  

---

## 📝 Problem Description
Given the root of a binary tree, the task is to find its maximum depth. The maximum depth is defined as the number of nodes along the longest path from the root node down to the farthest leaf node.

---

## 💡 Key Idea
The classic and most elegant solution is a "bottom-up" recursive approach. The function `maxDepth(node)` is designed to answer one simple question: "What is the maximum depth from this node downwards?"

1.  **Base Case:** If a node is `null`, it represents the end of a path, and its depth is `0`.
2.  **Recursive Step:** For any given node, its maximum depth is `1` (counting the node itself) plus the maximum depth of its left and right subtrees. We find these by recursively calling `maxDepth` on its children.

The final result is obtained by returning `1 + Math.max(maxDepth(node.left), maxDepth(node.right))`.

---

## 🧮 Complexity Analysis
- **Time:** O(N), where N is the total number of nodes in the tree, because we must visit every node exactly once.
- **Space:** O(H), where H is the height of the tree. This space is consumed by the recursion call stack. In a balanced tree, this is O(log N), but in the worst case (a skewed tree), it can be O(N).

---

## 📖 Notes
- **Real-world analogy:** Imagine an explorer mapping a building with many floors and branching corridors. To find the highest floor, they recursively explore each path. The total height from any point is 1 plus the maximum height of the paths branching off from there.
- **Alternative approach:** An iterative solution using **Breadth-First Search (BFS)** is also common. It involves traversing the tree level by level and simply counting the number of levels. This can be advantageous for extremely deep trees where a recursive approach might risk a stack overflow.
