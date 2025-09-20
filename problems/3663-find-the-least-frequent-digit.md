# 3663. Find The Least Frequent Digit

**Difficulty:** Easy  
**Algorithm:** Hash Map  
**Data Structure:** Hash Map  
**Date:** 2025-09-20  

---

## 📝 Problem Description
Given a number, find the digit that appears least frequently within it. If there is a tie for the least frequent digit, the smaller digit should be returned.

---

## Real-world analogy
Imagine you are running a small election and need to find the candidate with the fewest votes. If there's a tie for the fewest votes, you choose the candidate whose name comes first alphabetically (which is like choosing the smaller number).

A simple way is to first count every single ballot and create a complete tally sheet. After you've counted all the votes, you scan the entire tally sheet to find the winner based on your rules (lowest count, then smallest name/number).

---

## 💡 Key Idea
The most straightforward and optimal approach is a **two-pass strategy using a hash map**:

1.  **First Pass:** Iterate through each digit of the number. Use a hash map to store the frequency of each digit. The digit is the key, and its count is the value.
2.  **Second Pass:** Iterate through the entries in the completed hash map. Keep track of the lowest frequency found so far and the corresponding digit. If you find a digit with a lower frequency, it becomes the new answer. If you find a digit with the same lowest frequency, update your answer only if the current digit is smaller than the stored answer.

---

## 🧮 Complexity Analysis
- **Time:** `O(L)`, where L is the number of digits in the input number. The first pass is O(L) to build the map, and the second pass is O(K) where K is the number of unique digits (at most 10). This simplifies to O(L).
- **Space:** `O(1)`, because the hash map will store at most 10 digit-frequency pairs, which is constant space.

---

## 📖 Notes
- This problem is a great example of using a hash map for efficient frequency counting.
- The two-pass approach is optimal in terms of time complexity and provides a clean, readable solution by separating the logic of counting from the logic of finding the minimum.
