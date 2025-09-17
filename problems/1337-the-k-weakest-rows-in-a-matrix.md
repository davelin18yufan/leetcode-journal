# 1337. The K Weakest Rows in a Matrix

**Difficulty:** Easy  
**Algorithm:** Binary Search, Sorting  
**Data Structure:** Array, Matrix  
**Date:** 2025-09-17  

---

## 📝 Problem Description
The problem requires us to find the `k` weakest rows in a binary matrix. A row is considered weaker than another if it has fewer soldiers (represented by `1`s). If two rows have the same number of soldiers, the one with the smaller original index is considered weaker.

---

## 💡 Key Idea
The core idea is to determine the "strength" of each row by counting its soldiers. Since all `1`s appear before all `0`s in each row, this count can be found efficiently using **binary search** to locate the first `0`. Each row's strength is stored along with its original index.

After calculating the strengths, the list of rows is sorted based on the weakness criteria:
1.  Primary sort key: Number of soldiers (ascending).
2.  Secondary sort key (tie-breaker): Original row index (ascending).

Finally, we select the first `k` elements from this sorted list to get the indices of the weakest rows.

---

## 🧮 Complexity Analysis
- **Time:** O(M log N + M log M), where M is the number of rows and N is the number of columns. O(M log N) for counting soldiers using binary search across all rows, and O(M log M) for sorting the rows.
- **Space:** O(M) to store the strength and index for each row.

---

## 📖 Notes
- **Real-world analogy:** This is like organizing a playoff tournament. You have a list of teams, and their strength is their number of wins. To find the `k` weakest teams for the first round, you rank them by the fewest wins. If two teams have the same number of wins, the one listed earlier in the original schedule (lower index) is ranked lower as a tie-breaker.
- **Edge cases considered:** An empty matrix, `k` being 0, or a matrix with a single row/column. The binary search and sort approach handles these cases correctly.
