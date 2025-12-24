# 226. Invert Binary Tree

**Difficulty:** Easy  
**Algorithm:** Depth-First Search, Breadth-First Search  
**Data Structure:** Binary Tree  
**Date:** 2025-12-24  

---

## 📝 Problem Description
This problem requires inverting a binary tree. This means that for every node in the tree, its left and right children are swapped. The process is applied recursively to all nodes, effectively creating a mirror image of the original tree structure.

---

## Real-world analogy
A great real-world analogy is mirroring a user interface for languages that are read from right to left (RTL), such as Arabic or Hebrew. When a user switches their device's language from English (LTR) to an RTL language, the entire UI layout needs to be flipped horizontally. If the UI components are organized in a tree-like hierarchy (similar to a DOM tree), inverting this tree is the core logic needed to ensure that elements like side menus, icons, and text alignment are correctly mirrored for the RTL user.

---

## 💡 Key Idea
The core idea is to traverse the tree and swap the left and right children of each node. A recursive approach is very intuitive for this:
1.  Handle the base case: If the current node is `null`, do nothing and return.
2.  Swap the `left` and `right` children of the current node.
3.  Recursively call the invert function for the new left subtree and the new right subtree.

An iterative approach using a queue (Level Order Traversal/BFS) is also effective and avoids potential stack overflow issues with very deep trees.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the number of nodes in the tree, as each node must be visited once.
- Space: `O(H)`, where H is the height of the tree. This space is consumed by the recursion call stack. In the worst case of a skewed tree, this can be `O(N)`. For a balanced tree, it is `O(log N)`.

---

## 📖 Notes
- Real-world analogy: Mirroring a UI layout for RTL languages.
- This can be solved both recursively (DFS) and iteratively (BFS).
- The recursive solution's space complexity is tied to the height of the tree due to the call stack.
- Using modern destructuring assignment `[node.left, node.right] = [node.right, node.left]` can make the swap operation more concise.
