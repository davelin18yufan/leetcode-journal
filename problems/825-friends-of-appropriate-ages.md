# 825. Friends Of Appropriate Ages

**Difficulty:** Medium  
**Algorithm:** Two Pointers, Binary Search, Sorting  
**Data Structure:** Array  
**Date:** 2025-10-17  

---

## 📝 Problem Description

Given an array of integers `ages` representing the ages of a group of people, you need to find the total number of friend requests made. A request is made from person A to person B (A != B) if the following conditions are met:
- `age[B] <= 0.5 * age[A] + 7`
- `age[B] > age[A]`
- `age[B] > 100 && age[A] < 100` (This condition is implicitly covered by the second one)

---

## Real-world analogy

Imagine you're a data analyst at a massive convention with 20,000 attendees.

*   **Your Brute-Force (O(N²)) Approach:** You try to interview every single person and ask them to compare their age against all 19,999 other attendees. This will take forever.

*   **The Optimal (O(N)) Approach:** You're much smarter. You set up a table at the entrance with a simple census form, just a clipboard with ages 1 through 120. As each of the 20,000 people enters, they just make a tally mark next to their age. This first step takes `O(N)` time.

    Now, you don't care about the 20,000 individuals anymore. You just have your small clipboard with the age counts. You can now do your calculations. You just need to look at your 120 rows. For each age `ageX`, you compare it to every other age `ageY` on the list. This is only `120 * 120` (or `14,400`) comparisons, which is tiny and constant!

    If you find that `ageX=30` will request `ageY=25`, and your census says there are `50` people of age 30 and `100` people of age 25, you know that `50 * 100 = 5000` requests will be made, all in one simple calculation.

This "age counting" (or bucketing) is the key.

---

## 💡 Key Idea

The brute-force `O(N^2)` approach is too slow given `N` can be up to 20,000. The key insight is that the range of ages is very small (1 to 120). We can use an "age counting" or "bucketing" strategy.

1.  Create an array `ageCounts` of size 121 to store the frequency of each age.
2.  Iterate through the input `ages` once to populate this frequency map. This is `O(N)`.
3.  Iterate through all possible age pairs from 1 to 120 (`ageA`, `ageB`). This is a constant time operation (`120 * 120`).
4.  For each pair, check if a friend request can be made. If it can, add the number of requests to the total.
    *   If `ageA == ageB`, the number of requests is `count[ageA] * (count[ageA] - 1)`.
    *   If `ageA != ageB`, the number of requests is `count[ageA] * count[ageB]`.

This transforms the complexity from `O(N^2)` to `O(N + C^2)`, where `C` is the constant age range, effectively making it `O(N)`.

---

## 🧮 Complexity Analysis
- Time: `O(N + C^2)` where `N` is the number of people and `C` is the age range (120). This simplifies to `O(N)`.
- Space: `O(C)` for the `ageCounts` array, which is `O(1)` constant space.

---

## 📖 Notes
- Real-world analogy: Taking a census at a large event to analyze demographics efficiently instead of surveying every individual pair.
- The constraints on age are the most important clue to the optimal solution.
