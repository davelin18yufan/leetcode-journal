# 543. Diameter of Binary Tree

**Difficulty:** Easy  
**Algorithm:** Depth-First Search  
**Data Structure:** Tree  
**Date:** 2025-09-08  

---

## 📝 Problem Description
The "diameter" of a binary tree is the length of the longest path between any two nodes in the tree. This path may or may not pass through the root. The length of a path is the number of edges between the nodes.

---

## 💡 Key Idea
The core idea is to use a recursive Depth-First Search (DFS). For any given node, the longest path that passes *through* it is the sum of the heights of its left and right subtrees. The recursive function needs to perform two tasks simultaneously:
1.  **Return** the height of the subtree rooted at the current node to its parent.
2.  **Update** a global variable for the maximum diameter found so far by calculating `leftHeight + rightHeight` at each node.

This dual-purpose recursive function is a common and powerful pattern for solving tree problems.

---

## 🧮 Complexity Analysis
- **Time Complexity:** O(N), because the DFS function visits every node exactly once.
- **Space Complexity:** O(H), where H is the height of the tree. This space is used for the recursion call stack. In the worst-case scenario (a skewed tree), the height can be N, leading to O(N) space.

---

## 📖 Notes
- **Real-world analogy:** Imagine you are mapping a branching cave system. The "diameter" is the longest possible rope you could stretch between any two points in the cave. To find this, at any junction, you calculate the path length through your current position (left path + right path) and report your own depth back to the junction you came from.
- **Edge cases considered:** An empty tree, a tree with a single node, and a tree that is skewed (like a linked list).
- The key is realizing the recursive function must do two jobs: update a global diameter and return the local height.
