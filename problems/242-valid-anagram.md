# 242. Valid Anagram

**Difficulty:** Easy  
**Algorithm:** Hash Table, Sorting  
**Data Structure:** Hash Table, String  
**Date:** 2025-12-24  

---

## 📝 Problem Description
This problem requires checking if two strings are anagrams of each other, meaning they contain the same characters with the same frequencies, irrespective of order. For example, "anagram" and "nagaram" are anagrams.

---

## Real-world analogy
**Game Development: Word Puzzle & Cheat Detection**

Imagine developing a game like Scrabble or a text-based adventure. Players might claim to form a complex word from a given set of letters. The system needs to quickly verify if the two strings (the player's letters and the claimed word) are composed of the *exact same letters with the exact same frequencies*. This extends beyond simple equality checks. In anti-cheat systems, it can detect if users are manipulating permutations to bypass filters. In search engines, it can help find keywords that are similar in spelling but different in order.

---

## 💡 Key Idea
The most efficient way to determine if two strings are anagrams is to use a frequency counting approach, leveraging a single hash map (or an array if the character set is limited, e.g., 26 English letters).

1.  **Base Case:** First, check if the lengths of the two strings `s` and `t` are different. If they are, they cannot be anagrams, so return `false`.
2.  **Frequency Count:** Iterate through both strings simultaneously (or iterate through one, then the other). For each character in `s`, increment its count in the hash map. For each character in `t`, decrement its count.
3.  **Validation:** After processing both strings, iterate through the values in the hash map. If all character counts are `0`, it means every character that appeared in `s` also appeared in `t` with the same frequency, and vice-versa. Thus, the strings are anagrams, and you return `true`. Otherwise, return `false`.

This single hash map approach is robust and inherently supports Unicode characters without needing special handling for character sets larger than the English alphabet.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the length of the longer string. This is because we iterate through both strings (which have equal length if they are anagrams) once to build and update the frequency map, and then iterate through the map (at most `O(K)` where K is the number of unique characters, but in practice often considered constant for typical character sets like ASCII or Unicode, though strictly `O(K)`).
- Space: `O(1)` for a fixed-size character set (e.g., ASCII or 26 English letters, where an array can be used). More generally, `O(K)` where K is the number of unique characters in the strings (e.g., for Unicode characters when using a hash map).

---

## 📖 Notes
- Real-world analogy: Word puzzle games, cheat detection in text-based systems.
- A single hash map approach is generally more efficient and scalable than using two separate hash maps or sorting the strings.
- Using a `Map<string, number>` naturally supports Unicode characters, which is a significant advantage over fixed-size arrays for frequency counting.
- An alternative, though generally less efficient (due to `O(N log N)` sorting time complexity), is to sort both strings and then compare them.
