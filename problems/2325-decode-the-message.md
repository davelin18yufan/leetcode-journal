# 2325. Decode the Message

**Difficulty:** Easy
**Algorithm:** Hash Table, String
**Data Structure:** Hash Table, String
**Date:** 2025-10-06

---

## 📝 Problem Description
You are given the strings `key` and `message`, which represent a substitution cipher.

The `key` contains a permutation of the first 26 lowercase English letters. The first time each letter appears in the `key`, it establishes a mapping to a regular alphabet letter, starting with 'a'. For example, the first unique letter in the key maps to 'a', the second unique letter maps to 'b', and so on. Spaces map to spaces.

Your task is to decode the `message` using this substitution table.

---

## Real-world analogy
This problem is exactly like creating and using a **secret decoder ring**.

1.  **Step 1: Create the Decoder Ring (Building the Map)**

    *   The `key` string is a secret phrase, like `"the quick brown fox..."`.
    *   You take a blank decoder ring. You read the secret phrase one letter at a time.
    *   The first unique letter you see, `'t'`, you etch onto the outer wheel and align it with `'a'` on the inner wheel.
    *   The next unique letter, `'h'`, you align with `'b'`. The next, `'e'`, with `'c'`. You ignore spaces and any letter you've already put on the ring.
    *   This process of building the decoder is simulated by creating a substitution map.

2.  **Step 2: Use the Decoder Ring (Decoding the Message)**

    *   Now you receive the secret `message`.
    *   For each letter in the message, you find it on the outer wheel of your ring and write down the corresponding inner-wheel letter.
    *   The second loop in the code does exactly this, using the map for quick lookups.

---

## 💡 Key Idea
The core idea is a two-pass approach. 

1.  **First Pass:** Build a substitution map (a hash table). Iterate through the `key` string. For each character, if it's not a space and has not been seen before, map it to the next available letter of the alphabet (a, b, c...). A separate index variable can track the current alphabet letter.
2.  **Second Pass:** Decode the `message`. Iterate through the `message` string. For each character, if it's a space, append a space to the result. Otherwise, look up its substitution in the map and append the corresponding decoded letter.

---

## 🧮 Complexity Analysis
- Time: `O(M + N)`, where M is the length of the `key` and N is the length of the `message`. We need one pass for the key and one for the message.
- Space: `O(1)` auxiliary space, as the substitution map will store at most 26 key-value pairs, which is a constant.

---

## 📖 Notes
- Real-world analogy: Creating and using a secret decoder ring.
- The use of a hash map provides an efficient O(1) lookup time during the decoding phase, making the overall solution optimal.
