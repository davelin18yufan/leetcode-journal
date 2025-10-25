# 3106. Lexicographically Smallest String After Operations With Constraint

**Difficulty:** Medium  
**Algorithm:** Greedy  
**Data Structure:** String  
**Date:** 2025-10-25  

---

## 📝 Problem Description
(Short summary of problem in your own words.)
Given a string `s` and an integer `k`, you can perform an operation on a character of the string. In one operation, you can change a character to its previous character in the alphabet (e.g., 'b' becomes 'a', 'a' becomes 'z'). You can perform this operation at most `k` times. Find the lexicographically smallest string you can obtain.

---

## Real-world analogy
Imagine you have a combination lock with letters (`s`). You want to change the combination to the "smallest" possible one alphabetically (like "aaaaa...") but you only have `k` "clicks" you can turn the dials in total. Each click changes a letter by one step (e.g., 'c' to 'b' is 1 click, 'c' to 'a' is 2 clicks). Crucially, the dials wrap around ('a' to 'z' is 1 click).

Your strategy should be:

1.  Look at the **first dial** (`s[0]`). What's the cost (minimum clicks) to turn it to 'a'?
2.  Do you have enough clicks (`k`)?
      * **Yes:** Turn it to 'a'. Subtract the cost from `k`. Move to the next dial.
      * **No:** You can't reach 'a'. Use all your remaining `k` clicks to turn this dial as close to 'a' as possible (e.g., if you're at 'd' and have `k=2` clicks, turn it to 'b'). You now have 0 clicks left. You're done with this dial, and all subsequent dials must stay as they are.
3.  Repeat for the next dial until you run out of clicks or reach the end.

---

## 💡 Key Idea
The best way is a greedy approach. Iterate from left to right, changing each character as close to 'a' as possible using the available `k`.

---

## 🧮 Complexity Analysis
- Time: `O(N)` 
- Space: `O(N)`

---

## 📖 Notes
- Real-world analogy: Adjusting a combination lock with a limited number of clicks.
- Edge cases considered: `k` is 0, `k` is large enough to make the whole string "a...".
