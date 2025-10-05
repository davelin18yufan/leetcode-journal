# 1021. Remove Outermost Parentheses

**Difficulty:** Easy  
**Algorithm:** Stack Simulation  
**Data Structure:** Stack  
**Date:** 2025-10-05  

---

## 📝 Problem Description
Given a valid parentheses string `s`, consider its primitive decomposition. A primitive valid parentheses string is a nonempty valid parentheses string that cannot be split into two nonempty valid parentheses strings. The task is to remove the outermost parentheses of every primitive string in the primitive decomposition of `s`.

---

## Real-world analogy
This problem is like **peeling the outer layers of Russian nesting dolls (Matryoshka dolls)** that are lined up in a row.

  * The input string `s` is the full line of dolls, like `(()())` `(())`.
  * Each primitive string (`(()())` and `(())`) is one complete doll set.
  * The problem asks you to remove the **outermost doll** from each set and then concatenate what's left inside.

A counter tracks how many layers deep you are. You only keep the parts of the dolls that are not on the outermost layer. When you see an opening parenthesis `(`, you go one layer deeper. If you were already inside a doll, this new `(` is an inner layer, so you keep it. When you see a closing parenthesis `)`, you are about to come out one layer. If your current depth is greater than 1, the `)` you're looking at is an inner layer, so you keep it.

---

## 💡 Key Idea
The core idea is to iterate through the string while maintaining a counter to track the balance of parentheses, which represents the current depth. We append a parenthesis to the result only when it is not part of the outermost layer of a primitive component. An opening parenthesis is added if the balance is greater than 0 before incrementing. A closing parenthesis is added if the balance is greater than 1 before decrementing (or greater than 0 after decrementing). This effectively simulates a stack with a simple counter for efficiency.

---

## 🧮 Complexity Analysis
- Time: `O(N)` 
- Space: `O(N)` (for the output string, auxiliary space is `O(1)`)

---

## 📖 Notes
- Real-world analogy: Peeling the outer layers of Russian nesting dolls.  
- Edge cases considered: The input is always a valid parentheses string.
