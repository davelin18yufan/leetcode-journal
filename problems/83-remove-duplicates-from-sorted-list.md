# 83. Remove Duplicates from Sorted List

**Difficulty:** Easy
**Algorithm:** Single Pointer
**Data Structure:** Linked List
**Date:** 2025-09-02

---

## 📝 Problem Description
Given the `head` of a sorted linked list, the task is to delete all duplicate elements such that each element appears only once. The resulting linked list should still be sorted.

---

## 💡 Key Idea
The optimal approach is to use a single pointer, let's call it `current`, to traverse the list. This method modifies the list "in-place" to save space. The core logic is to "look ahead": while standing at a `current` node, we check the value of the `current.next` node. If the values are the same, we skip the duplicate by changing `current.next` to point to `current.next.next`. If the values are different, we are safe to advance our `current` pointer to the next node. This process is repeated until the end of the list is reached.

---

## 🧮 Complexity Analysis
- **Time:** O(N), as we traverse the list once from beginning to end.
- **Space:** O(1), because the modification is done in-place, using only a single extra pointer.

---

## 📖 Notes
- **Real-world analogy:** Imagine you're the conductor of a long train where cars are sorted by color. To remove duplicate cars, you stand in one car (`current`) and look at the next. If it's the same color, you have it unhooked and connect yours to the one after it. If it's a different color, you just walk to the next car. This one-pass, in-place process is exactly how the algorithm works.
- **Edge cases considered:** An empty list, a list with no duplicates, and lists with multiple consecutive duplicates (e.g., `[1, 1, 1]`). The "look-ahead" check must also ensure the `next` node is not `null` before accessing its value.
