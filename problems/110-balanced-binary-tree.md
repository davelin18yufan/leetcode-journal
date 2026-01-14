# 110. Balanced Binary Tree

**Difficulty:** Easy  
**Algorithm:** Depth-First Search  
**Data Structure:** Tree, Binary Tree
**Date:** 2026-01-14  

---

## 📝 Problem Description
Given a binary tree, determine if it is height-balanced. A height-balanced binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.

---

## Real-world analogy
Maintaining a balanced binary tree is essential for database indexing to ensure search operations stay at O(log n) efficiency. When data is frequently added, a B-Tree or AVL Tree index might become "skewed". If the tree isn't balanced, search performance degrades to O(n), similar to traversing a linked list. Database systems periodically check for balance and trigger "rotations" to rebalance the tree, guaranteeing optimal query speed.

---

## 💡 Key Idea
The approach uses a Bottom-up Depth-First Search (DFS). For each node, we recursively calculate the height of its left and right subtrees. If a subtree is already unbalanced (which we can signify by returning -1), or if the absolute difference in heights between the left and right subtrees is more than 1, we immediately know the entire tree is unbalanced and propagate this information up by returning -1. Otherwise, we return the height of the current node's subtree.

---

## 🧮 Complexity Analysis
- Time: `O(N)` 
- Space: `O(H)` where H is the height of the tree.

---

## 📖 Notes
- Real-world analogy: Database index rebalancing to maintain fast query performance.  
- Edge cases considered: null root, single node tree, skewed tree.
