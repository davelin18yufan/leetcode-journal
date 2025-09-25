# 100. Same Tree

**Difficulty:** Easy  
**Algorithm:** Depth-First Search, Breadth-First Search  
**Data Structure:** Tree, Binary Tree  
**Date:** 2025-09-25  

---

## 📝 Problem Description
Given the roots of two binary trees, `p` and `q`, write a function to check if they are the same or not. Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

---

## Real-world analogy
Think of this problem as comparing two company **organization charts** to see if they are identical.

To verify they're the same, you would:

1.  **Start at the top:** Are the two CEOs (`root` nodes) the same person? If one chart has a CEO and the other doesn't, they're not identical.
2.  **Check the Left Branch:** You then look at the entire division managed by the CEO's left-hand report. Is that entire division's structure and personnel identical in both charts? You apply the same top-down check recursively for this entire branch.
3.  **Check the Right Branch:** You do the same for the CEO's right-hand report's entire division.

The two org charts are only identical if the CEOs match, **AND** their entire left branches match, **AND** their entire right branches match. Your recursive code perfectly models this logic.

---

## 💡 Key Idea
The core idea is to use recursion. We check three conditions at each level:
1.  Are the current nodes `p` and `q` both null? If so, they are the same at this branch.
2.  Is one of them null, or are their values different? If so, the trees are not the same.
3.  Recursively call the function on the left children (`p.left`, `q.left`) and the right children (`p.right`, `q.right`). The trees are only the same if both of these recursive calls return `true`.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the number of nodes in the smaller tree, as we have to visit each node once.
- Space: `O(H)`, where H is the height of the tree, due to the recursion stack. In a skewed tree, this can be `O(N)`.

---

## 📖 Notes
- Real-world analogy: Comparing two organization charts for identical structure and roles.
- This is a classic example of a structural recursion problem on trees. The base cases (null nodes) and the recursive step (checking children) are fundamental.
