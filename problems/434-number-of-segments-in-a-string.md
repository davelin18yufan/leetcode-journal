# 434. Number of Segments in a String

**Difficulty:** Easy  
**Algorithm:** String, Single Pass  
**Data Structure:** N/A  
**Date:** 2025-09-30  

---

## 📝 Problem Description
Given a string, count the number of "segments" in it. A segment is defined as a contiguous sequence of non-space characters.

---

## Real-world analogy
This problem is like counting the cars in a freight train. The letters are the cargo, and the spaces are the empty gaps between the cars. You want to count the number of distinct cars. You walk along the train, and you only add to your tally when you step onto the beginning of a new car. You know you're at the beginning of a new car if you're standing on cargo (a non-space character) and the spot right behind you was either an empty gap (a space) or the very beginning of the train.

---

## 💡 Key Idea
The core insight is to count the start of each segment. A segment starts when a non-space character is encountered, and it is either the first character of the string or is preceded by a space. This allows for a single pass through the string with constant extra space.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the length of the string, because we perform a single pass.
- Space: `O(1)`, as we only use a few variables to keep track of the count, not proportional to the input size.

---

## 📖 Notes
- Real-world analogy: Counting words in a sentence where words are separated by spaces.
- Edge cases considered: empty string, string with only spaces, leading/trailing spaces, and multiple spaces between segments.
