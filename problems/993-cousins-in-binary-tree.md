# 993. Cousins in Binary Tree

**Difficulty:** Easy
**Algorithm:** BFS
**Data Structure:** Tree, Queue
**Date:** 2025-09-06

---

## 📝 Problem Description
Given the root of a binary tree with unique values, and the values of two different nodes `x` and `y`. Two nodes of a binary tree are cousins if they have the same depth with different parents.

---

## 💡 Key Idea
The most direct approach for problems involving levels or depths is a Breadth-First Search (BFS). We can traverse the tree level by level using a queue. In each level, we check if we find both `x` and `y`. Crucially, we must also verify they don't have the same parent. This can be done by checking if any node's left and right children are `x` and `y`.

---

## 🧮 Complexity Analysis
- **Time:** O(N), where N is the number of nodes, as each node is visited once.
- **Space:** O(W), where W is the maximum width of the tree. This space is for the queue, which at its peak holds all nodes at the widest level of the tree.

---

## 📖 Notes
- **Real-world Analogy:** Imagine a genealogist checking if two people, Alice and Bob, are cousins. They need to confirm two facts: 1) Are Alice and Bob in the same generation (same depth in the family tree)? 2) Do they have different parents? If both are true, they are cousins. BFS is like checking the family tree generation by generation.
- **Key Insight:** BFS is a natural fit for level-based tree problems. It allows checking all nodes at a certain depth before moving to the next, making it easy to compare nodes at the same level.
