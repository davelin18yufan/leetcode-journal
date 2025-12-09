# 2423. Remove Letter To Equalize Frequency

**Difficulty:** Easy
**Algorithm:** Counting, Simulation
**Data Structure:** Hash Table, String
**Date:** 2025-12-09

---

## 📝 Problem Description

You are given a 0-indexed string `word`. You need to select one index and remove the character at that index. The goal is to make the frequencies of all remaining characters in the resulting string equal. Return `true` if this is possible, otherwise return `false`.

---

## Real-world analogy

Imagine a factory that produces different colored toy blocks. For a batch to be 'perfectly balanced', all colors present must have the exact same number of blocks. You are given a batch that is almost balanced, but might have one extra block of a certain color, or a single block of a unique color. Your task is to determine if you can achieve a perfectly balanced batch by removing just one single block. This is similar to inventory management where you check if a dataset becomes consistent after removing a single outlier.

---

## 💡 Key Idea

The most straightforward approach is to use simulation. Since the word length is small, we can afford to try removing each character one by one and checking if the resulting string meets the condition.

The process is as follows:
1.  Iterate through each character of the input `word` from index `0` to `N-1`, where `N` is the length of the word.
2.  In each iteration, simulate the removal of the character at the current index.
3.  For the resulting temporary string, build a frequency map of its characters.
4.  Check if all values (frequencies) in the map are identical.
5.  If they are identical, it means we have found a valid removal. We can immediately return `true`.
6.  If the loop completes without finding any such case, it means no single character removal can satisfy the condition, so we return `false`.

---

## 🧮 Complexity Analysis

- Time: `O(N^2)`, where N is the length of the word. The outer loop runs N times. Inside the loop, building the frequency map takes O(N) time.
- Space: `O(1)`, as the frequency map will store at most 26 unique lowercase English letters.

---

## 💻 Code

```typescript
function equalFrequency(word: string): boolean {
    const N = word.length;

    // Simulate removing one character at every possible index i
    for (let i = 0; i < N; i++) {
        const charToRemove = word[i];
        
        // 1. Build the frequency map for the string *after* removal
        const freqMap = new Map<string, number>();
        for (let j = 0; j < N; j++) {
            if (i === j) {
                // Skip the character being removed
                continue;
            }
            freqMap.set(word[j], (freqMap.get(word[j]) || 0) + 1);
        }

        // 2. Check the condition: Are all remaining frequencies equal?
        if (freqMap.size === 0) {
            // This can happen if the original word had 1 character.
            // For an empty result, the frequencies are vacuously equal.
            return true;
        }

        // Get the first frequency we encounter to use as the target
        let targetFreq = 0;
        let allEqual = true;

        for (const freq of freqMap.values()) {
            if (targetFreq === 0) {
                targetFreq = freq; // Initialize the target frequency
            } else if (freq !== targetFreq) {
                allEqual = false;
                break;
            }
        }

        // 3. If all remaining frequencies are equal, we found a solution
        if (allEqual) {
            return true;
        }
    }

    // If no single removal worked after checking all N possibilities
    return false;
}
```