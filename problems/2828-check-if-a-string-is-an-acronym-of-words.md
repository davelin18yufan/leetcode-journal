# 2828. Check if a String Is an Acronym of Words

**Difficulty:** Easy
**Algorithm:** String Manipulation
**Data Structure:** Array, String
**Date:** 2025-10-06

---

## 📝 Problem Description
Given an array of strings `words` and a string `s`, determine if `s` is an acronym of `words`. The string `s` is considered an acronym of `words` if it can be formed by concatenating the first character of each string in `words` in order.

---

## Real-world analogy
This problem is like checking a receipt against your shopping list to make sure the cashier rang everything up.

  * The `words` array is your shopping list: `["Apples", "Bananas", "Cherries"]`.
  * The string `s` is a shorthand code printed on the receipt: `"abc"`.

To verify the receipt, you do exactly what the algorithm does:

1.  **First, you do a quick sanity check:** Does the number of items on your list match the number of letters in the code? If not, it's definitely wrong. This is the `if(words.length !== s.length)` check—a crucial first step.
2.  **Then, you go item by item:** Does the first item ("**A**pples") start with the first letter of the code ('**a**')? Yes. Does the second item ("**B**ananas") start with the second letter ('**b**')? Yes. And so on.

You only need to go through your list once to verify it, which is what an efficient `for` loop does.

---

## 💡 Key Idea
The core idea is to perform a direct comparison between the number of words and the length of the acronym string. If they don't match, it's impossible for it to be a valid acronym. If they do match, iterate through the words and the string simultaneously, checking if the first character of each word matches the corresponding character in the string. If any mismatch is found, return false immediately. If the loop completes, it's a valid acronym.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the number of words. We must iterate through each word once.
- Space: `O(1)`, as no extra space is used that scales with the input size.

---

## 📖 Notes
- Real-world analogy: Verifying a shorthand code (like "abc") against a list of full words (["Apples", "Bananas", "Cherries"]).
- Edge cases considered: The number of words not matching the length of the acronym string.
