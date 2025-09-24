# 2744. Find Maximum Number of String Pairs

**Difficulty:** Easy  
**Algorithm:** Simulation  
**Data Structure:** Hash Table  
**Date:** 2025-09-24  

---

## 📝 Problem Description
Given a 0-indexed array of unique strings `words`, return the number of pairs of strings that are the reverse of each other. For example, "cd" and "dc" are a pair.

---

## Real-world analogy
This problem is exactly like **pairing socks from a pile of laundry**.

Imagine you have a big pile of unique socks (`words`). Your goal is to make as many pairs as possible.

  * **Your Algorithm:** You get an empty laundry basket (your `Set`). You pick up one sock from the pile (`w`). You look inside your basket to see if its matching sock (the reversed string `s`) is already there.
      * **If YES:** You've found a match! You take the sock out of the basket, put the pair together, and add one to your `output` count. You don't put the sock you're holding into the basket because it's now paired.
      * **If NO:** This sock doesn't have a match in the basket yet. You place it in the basket (`set.add(w)`), hoping its mate will appear later in the pile.

You repeat this process for every sock. At the end, `output` is the number of pairs you've successfully made.

---

## 💡 Key Idea
Use a `Set` to efficiently store and check for the existence of strings we've already seen. For each word, we calculate its reverse. If the reversed version of the current word exists in our set, we've found a pair. Otherwise, we add the current word to the set so a future word can be paired with it.

---

## 🧮 Complexity Analysis
- Time: `O(N)` 
- Space: `O(N)`

---

## 📖 Notes
- Real-world analogy: Pairing socks from a pile of laundry.  
- Edge cases considered: empty input array, words with no pairs.
