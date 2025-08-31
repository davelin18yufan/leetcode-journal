# 728. Self Dividing Numbers

**Difficulty:** Easy  
**Algorithm:** Math  
**Data Structure:** N/A  
**Date:** 2025-08-31  

---

## 📝 Problem Description
The task is to find all "self-dividing" numbers within a given range `[left, right]`. A number is defined as self-dividing if it is evenly divisible by every single digit it contains. A crucial rule is that a self-dividing number is not allowed to contain the digit zero.

---

## 💡 Key Idea
The optimal approach is to iterate through each number in the given range and check if it meets the self-dividing criteria. For each number, its digits can be extracted mathematically using a loop with the modulo (`% 10`) and integer division (`Math.floor(current / 10)`) operations. For each extracted digit, two conditions must be verified: 1) the digit is not zero, and 2) the original number is divisible by the digit. If all digits pass, the number is added to the result list.

---

## 🧮 Complexity Analysis
- **Time:** O(D * log₁₀(R)), where D is the number of elements in the range (`right - left`) and R is the upper bound `right`. Since `log₁₀(R)` (the number of digits) is a small constant for the given constraints, the complexity is effectively linear in the size of the range, O(D).
- **Space:** O(K), where K is the number of self-dividing numbers found. This space is used for the output array. Excluding the result, the space complexity is O(1).

---

## 📖 Notes
- **Real-world analogy:** This is like a quality control check for custom "premium" phone numbers. A number is premium if the full number is divisible by each of its digits (excluding zero). To verify a range of numbers, you must inspect each one individually and test its digits against the rule, just as the algorithm does.
- **Edge cases considered:** The primary edge case is a number containing the digit zero, which immediately disqualifies it. The logic must explicitly check for this.
