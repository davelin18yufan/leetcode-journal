# 235. Lowest Common Ancestor of a Binary Search Tree

**Difficulty:** Medium
**Algorithm:** Depth-First Search, Binary Search Tree
**Data Structure:** Tree, Binary Tree
**Date:** 2026-01-08

---

## 📝 Problem Description
Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST. The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in the tree that has both `p` and `q` as descendants.

---

## Real-world analogy
A good real-world analogy is finding the nearest common manager in a corporate organizational chart. If the company's org chart is structured like a BST (e.g., by employee ID), and you need to find the closest manager to two employees, 'p' and 'q', to resolve a dispute. If both employees are in the manager's left subtree (their IDs are smaller), you'd search down that branch. If one is in the left and one is in the right, that manager is the LCA. This is also similar to how Git finds a common base commit for merging two branches.

---

## 💡 Key Idea
The key insight is to leverage the properties of a Binary Search Tree. Starting from the root, if both nodes `p` and `q` have values smaller than the current node, their LCA must be in the left subtree. If both have larger values, the LCA must be in the right subtree. The first node encountered where `p` and `q` are on opposite sides (one smaller, one larger) is the "split point" and therefore the Lowest Common Ancestor. This allows for a targeted search instead of a full tree traversal.

---

## 🧮 Complexity Analysis
- Time: `O(H)`, where H is the height of the tree. In the worst case of a skewed tree, this becomes `O(N)`.
- Space: `O(1)` for the iterative approach, or `O(H)` for the recursive approach due to the call stack.

---

## 📖 Notes
- Real-world analogy: Finding the nearest common manager in an org chart or a base commit in Git.
- Edge cases considered: One node being the ancestor of the other, skewed tree. The iterative approach is preferred for space optimization (`O(1)`).
- This is a classic interview question that tests understanding of BST properties. A follow-up could be to solve it for a regular Binary Tree (LeetCode 236), which would require a different approach.
