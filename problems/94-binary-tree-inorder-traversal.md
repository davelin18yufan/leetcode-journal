# 94. Binary Tree Inorder Traversal

**Difficulty:** Easy
**Algorithm:** DFS, Recursion
**Data Structure:** Tree, Stack
**Date:** 2025-09-06

---

## 📝 Problem Description
Given the root of a binary tree, return the inorder traversal of its nodes' values. The inorder traversal follows the sequence: visit the left subtree, visit the root node, then visit the right subtree.

---

## 💡 Key Idea
The standard and most intuitive way to solve this is using recursion. A helper function is defined to traverse the tree. For any given node, the function first calls itself on the left child, then processes the node's own value by adding it to a result list, and finally calls itself on the right child. A base case where the node is `null` stops the recursion.

---

## 🧮 Complexity Analysis
- **Time:** O(N), as every node in the tree is visited exactly once.
- **Space:** O(N) in the worst case for the recursion call stack (for a completely skewed tree). For a balanced tree, the space complexity is O(log N).

---

## 📖 Notes
- **Real-world Analogy:** Imagine a librarian listing books on a shelf following a strict `Left -> Self -> Right` rule for every book and its sub-sections. They must completely finish the left section before listing the current book, and only after listing the current book do they move to the right section. This recursive process ensures the final list is in the correct "inorder" sequence.
- **Alternative:** An iterative solution using an explicit stack can avoid deep recursion and potential stack overflow issues. It simulates the recursive calls manually.
