# 2535. Difference Between Element Sum and Digit Sum of an Array

**Difficulty:** Easy  
**Algorithm:** Math  
**Data Structure:** Array  
**Date:** 2025-10-31  

---

## 📝 Problem Description
Given an array of positive integers `nums`, return the absolute difference between the element sum and the digit sum of `nums`.

---

## Real-world analogy
Imagine you have a stack of checks (`nums`).
- **Element Sum:** The total dollar value of all checks.
- **Digit Sum:** A strange "numerology" sum where you add up all the individual digits written on the checks (e.g., a `$15` check adds `1+5=6`).
The problem asks for the absolute difference between the total value and the total numerology sum.

---

## 💡 Key Idea
The core idea is to calculate two separate sums:
1.  **Element Sum:** The sum of all numbers in the array.
2.  **Digit Sum:** The sum of all digits that make up those numbers.

To get the digit sum of a number, you can repeatedly take the number modulo 10 (to get the last digit) and then divide the number by 10 (to remove the last digit), until the number becomes 0.

Finally, calculate the absolute difference between these two sums.

---

## 🧮 Complexity Analysis
- Time: `O(N * L)`, where N is the number of elements and L is the average number of digits in each element. Since `L` is small and constant for typical integer sizes, this simplifies to `O(N)`.
- Space: `O(1)` if calculating the digit sum mathematically. `O(L)` if converting numbers to strings.

---

## 📖 Notes
- Real-world analogy: Calculating the difference between the face value of checks and the sum of their individual digits.
- Edge cases: The array can contain single-digit numbers, where the element sum and digit sum are the same for that number.
