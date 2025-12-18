# 21. Merge Two Sorted Lists

**Difficulty:** Easy
**Algorithm:** Recursion
**Data Structure:** Linked List
**Date:** 2025-12-18

---

## 📝 Problem Description
Given the heads of two sorted linked lists, merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

---

## Real-world analogy
This is equivalent to merging two pre-sorted data streams, such as log files from different servers. Imagine a large e-commerce platform where user click logs are stored on different servers for performance reasons. Each server's logs are already sorted by timestamp. When a data analyst needs a complete timeline of all platform activity, the backend system must merge these sorted log streams into a single, comprehensive, and sorted list. Using a linked list is efficient because it avoids loading all data into memory at once, instead splicing the data streams together node by node, which is crucial when dealing with massive datasets.

---

## 💡 Key Idea
The core idea is to recursively merge the two lists. At each step, compare the values of the current heads of both lists. The node with the smaller value becomes the head of the merged list. The `next` pointer of this smaller node is then set by making a recursive call with the remaining elements of the lists. The base case for the recursion is when either of the lists becomes null, at which point the other list is returned.

---

## 🧮 Complexity Analysis
- **Time:** `O(N + M)`, where N and M are the number of nodes in the two lists, as each node is visited exactly once.
- **Space:** `O(N + M)` for the recursive approach due to the call stack depth. An iterative approach can achieve `O(1)` space complexity.

---

## 📖 Notes
- **Real-world analogy:** Merging sorted log files from distributed systems.
- **Key Optimization:** An iterative approach using a "dummy head" node is preferred in production to avoid potential stack overflow with very long lists and to achieve `O(1)` space complexity.
- **Edge cases:** One or both lists are empty.