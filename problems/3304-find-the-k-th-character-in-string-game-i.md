# 3304. Find the K-th Character in String Game I

**Difficulty:** Easy  
**Algorithm:** Recursion, Bit Manipulation  
**Data Structure:** String  
**Date:** 2025-10-18  

---

## 📝 Problem Description
A string game involves generating a sequence of strings. Starting with `s_0 = "a"`, the string `s_i` is created by taking `s_{i-1}`, appending the result of transforming every character in `s_{i-1}` to its next letter in the alphabet (with 'z' wrapping around to 'a'). Given `k`, find the k-th character of the first string in this sequence that has a length of at least `k`.

---

## Real-world analogy
This problem is like **building a fractal pattern**.

1.  You start with a single line: **`a`** (Length 1)
2.  The next step, you take your *entire* current pattern ("a") and add a "transformed" copy of it ("b"). The result is **`ab`**. (Length 2)
3.  The next step, you take your *entire* current pattern ("ab") and add a "transformed" copy of it ("bc"). The result is **`abbc`**. (Length 4)
4.  The next step, you take "abbc" and add "bccd". The result is **`abbcbccd`**. (Length 8)

Notice the pattern: The string **doubles in length** each time. This is a huge clue that a divide-and-conquer or recursive approach is possible.

---

## 💡 Key Idea
Instead of building the potentially very long string, we can deduce the character at the k-th position recursively. The string at any step `m` is composed of the string from step `m-1` and a transformed version of the string from `m-1`. This means if `k` is in the first half, we look for the character in the previous generation's string. If `k` is in the second half, we find the corresponding character in the first half and then find its next character.

---

## 🧮 Complexity Analysis
- Time: `O(log k)`, because with each recursive step, we effectively cut the problem size in half.
- Space: `O(log k)`, due to the recursion depth.

---

## 📖 Notes
- The problem can be solved without actually constructing the string, which avoids memory and time issues for large `k`.
- The core of the solution is a recursive function that determines the character based on its position (`k`) relative to the half-length of the conceptual string.
- This is a good example of how problems involving self-similar, exponentially growing structures can often be solved with logarithmic time complexity.
