# 867. Transpose Matrix

**Difficulty:** Easy
**Algorithm:** Matrix Simulation
**Data Structure:** Array
**Date:** 2025-09-28

---

## 📝 Problem Description
Given a 2D integer array `matrix`, return the transpose of the `matrix`. The transpose of a matrix is the matrix flipped over its main diagonal, which means switching the row and column indices of the matrix.

---

## Real-world analogy
This problem is exactly like **rotating a spreadsheet**. Imagine you have a spreadsheet with data (your `matrix`). Transposing it means you're creating a new, blank spreadsheet where the number of rows and columns are swapped. Then, you go through your original sheet cell by cell. You copy the value from `(row i, column j)` and paste it into the new sheet at `(row j, column i)`.

---

## 💡 Key Idea
The core idea is to create a new matrix with swapped dimensions. If the original matrix has `m` rows and `n` columns, the new matrix will have `n` rows and `m` columns. Then, iterate through the original matrix and for each element at `matrix[i][j]`, place it in the new matrix at `transposedMatrix[j][i]`.

---

## 🧮 Complexity Analysis
- Time: `O(M * N)` - We must visit every element in the original matrix once.
- Space: `O(M * N)` - We need to create a new matrix of the same size to store the transposed result.

---

## 📖 Notes
- Real-world analogy: Rotating a spreadsheet or flipping an image's width and height.
- Edge cases considered: non-square matrices, single-row matrices, single-column matrices.
