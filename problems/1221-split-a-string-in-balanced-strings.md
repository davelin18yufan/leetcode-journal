# 1221. Split a String in Balanced Strings

**Difficulty:** Easy  
**Algorithm:** Greedy, Counting  
**Data Structure:** String  
**Date:** 2025-09-03  

---

## 📝 Problem Description
The problem asks us to split a string into the maximum number of balanced substrings. A balanced string is defined as a string that has an equal number of 'L' and 'R' characters.

---

## 💡 Key Idea
The core insight is to use a greedy approach. Since we want to maximize the number of splits, it's always optimal to split the string as soon as we find the shortest possible balanced prefix. We can achieve this with a single pass and a counter. We iterate through the string, incrementing the counter for one character (e.g., 'L') and decrementing for the other ('R'). Whenever the counter returns to zero, it signifies a balanced substring, and we can increment our split count.

---

## 🧮 Complexity Analysis
- Time: O(N), as we only need to iterate through the string once.
- Space: O(1), as we only use a few variables to keep track of the balance and split count, regardless of the input string's size.

---

## 📖 Notes
- **Real-world analogy:** Imagine you are walking on a path, taking a step left for 'L' and a step right for 'R'. A balanced string is a sequence of steps that brings you exactly back to your starting point. The greedy approach is like declaring a "segment" complete the moment you return to the start, allowing you to begin a new segment immediately. This ensures you find the maximum number of such segments in your total walk.
- **Edge cases considered:** An empty string would result in 0 splits. A string that is already balanced like "RLRL" will be split into "RL" and "RL". A string like "LLLLRRRR" is one single balanced string.
