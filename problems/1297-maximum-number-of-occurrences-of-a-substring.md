# 1297. Maximum Number of Occurrences of a Substring

**Difficulty:** Medium
**Algorithm:** Sliding Window, Hash Table, String
**Data Structure:** Hash Table
**Date:** 2025-11-09

---

## 📝 Problem Description
Given a string `s`, the goal is to find the maximum frequency of any substring that meets two conditions:
1. The number of unique characters in the substring is no more than `maxLetters`.
2. The length of the substring is between `minSize` and `maxSize` (inclusive).

---

## Real-world analogy
Imagine analyzing a very long DNA sequence to find the most frequently occurring gene segment. These segments must meet specific criteria: they can only contain a limited number of unique base pairs (`maxLetters`) and must have a length within a certain range (`minSize` to `maxSize`). By identifying the most common valid segment, scientists can pinpoint important genetic markers or repeated patterns that might be linked to specific traits or diseases. The problem simplifies this by realizing that if a long segment is frequent, its shorter prefixes will be at least as frequent, so we only need to check for the shortest possible length (`minSize`).

---

## 💡 Key Idea
The crucial insight is that the `maxSize` constraint is irrelevant. If a valid substring of length `k > minSize` occurs `F` times, then its prefix of length `minSize` must also occur at least `F` times. Therefore, the maximum frequency will always be associated with a substring of length `minSize`.

The approach is to iterate through the string with a sliding window of `minSize`, generating all substrings of that length. For each substring, we check if it satisfies the `maxLetters` condition. We use a hash map to store the frequency of each valid substring and keep track of the maximum frequency found so far.

---

## 🧮 Complexity Analysis
- Time: `O(N)` - We iterate through the string once. Although substring creation and checking unique characters inside the loop takes `O(minSize)`, the problem constraints state `minSize` is small (<= 26), making it a constant factor. Thus, the complexity is linear with respect to the length of `s`.
- Space: `O(M * minSize)` - Where `M` is the number of unique valid substrings. In the worst case, `M` can be proportional to `N`, so space is `O(N)`.

---

## 📖 Notes
- The `maxSize` parameter is a distraction, as the highest frequency will always be found with a substring of length `minSize`.
- A sliding window approach combined with a hash map is efficient for counting occurrences of substrings that meet the criteria.
