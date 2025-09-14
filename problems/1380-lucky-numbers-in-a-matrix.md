# 1380. Lucky Numbers in a Matrix

**Difficulty:** Easy
**Algorithm:** Matrix, Preprocessing
**Data Structure:** Array, Set
**Date:** 2025-09-14

---

## 📝 Problem Description
The problem requires finding all "lucky numbers" in an `m x n` matrix. A lucky number is defined as an element that is both the minimum element in its row and the maximum element in its column.

---

## 💡 Key Idea
The most direct and efficient approach is to use a two-pass preprocessing strategy. This cleanly separates the two conditions (row minimum, column maximum) and then finds the numbers that satisfy both.

1.  **First Pass (Row Minimums):** Iterate through each row of the matrix, find the minimum value, and store all these minimums in a `Set` for quick lookups.
2.  **Second Pass (Column Maximums):** Iterate through each column, find the maximum value, and do the same.
3.  **Intersection:** Finally, iterate through the set of row minimums and check for each value if it also exists in the set of column maximums. Any value present in both sets is a "lucky number".

---

## 🧮 Complexity Analysis
- **Time:** O(M * N) - We make two full passes over the matrix, which is proportional to the number of cells.
- **Space:** O(M + N) - We use two sets to store the minimums from M rows and the maximums from N columns.

---

## 📖 Notes
- **Real-world analogy:** This is equivalent to finding a **saddle point** on a topographical map. A saddle point is a location that is the lowest point along its own east-west path (the row) while simultaneously being the highest point on its north-south path (the column). It's a mountain pass that's a valley in one direction and a peak in another.
- **Edge cases:** The problem constraints state the matrix is not empty and contains positive integers, which simplifies the logic as we don't need to handle empty rows/columns or zero/negative values.
