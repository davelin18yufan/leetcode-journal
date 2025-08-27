# 21. Merge Two Sorted Lists

**Difficulty:** Easy
**Algorithm:** Recursion, Iteration
**Data Structure:** Linked List
**Date:** 2025-08-27

---

## 📝 Problem Description
Given the heads of two sorted linked lists, merge them into a single sorted linked list and return the head of the new list.

---

## 💡 Key Idea
The problem can be solved either recursively or iteratively.

- **Recursive Approach:** Compare the heads of the two lists. The node with the smaller value becomes the head of the merged list. Its `next` pointer is then set to the result of the recursive call on the remaining parts of the lists. The base case is when one of the lists is null, in which case the other list is returned.

- **Iterative Approach:** Use a dummy head node to simplify the process of building the new list. A `current` pointer tracks the end of the new list. In a loop, compare the nodes from both lists and append the smaller one to `current.next`. After the loop, append the remaining non-null list. This approach uses constant space.

---

## 🧮 Complexity Analysis
- **Recursive:**
  - Time: O(N + M), where N and M are the lengths of the two lists.
  - Space: O(N + M) due to the recursion call stack.
- **Iterative:**
  - Time: O(N + M)
  - Space: O(1)

---

## 📖 Notes
- Real-world analogy: Merging two sorted decks of cards by repeatedly picking the smaller of the top two cards.
- The iterative solution with a dummy head is generally preferred in an interview setting due to its O(1) space complexity, which avoids the risk of a stack overflow with very long lists.
- Edge cases: one or both lists are empty.
