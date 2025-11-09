1297. Maximum Number of Occurrences of a Substring
Medium
Hash Table
String
Sliding Window


-----

### \#\# 💡 The Optimal Solution

Your current code is *almost* the optimal solution. You just need to replace the sort. Instead of sorting, just iterate through the map's values and keep track of the max.

Here is how you can find the max frequency in one pass, replacing your `sort`:

```typescript
    if(map.size < 1) return 0;

    // O(M) pass, where M is map.size
    let maxFrequency = 0;
    for (const frequency of map.values()) {
        if (frequency > maxFrequency) {
            maxFrequency = frequency;
        }
    }
    
    return maxFrequency;
```

-----

### \#\# 🕵️ Complexity Analysis (Refined)

Your analysis was very close, but let's refine it based on the problem's constraints.

  * **Your Code's Loop:** `O(N * K)`
      * Your `for` loop runs `N` times (where `N = s.length`).
      * Inside the loop, you do:
        1.  `s.substring(i, i + minSize)`: This takes `O(K)` time (where `K = minSize`).
        2.  `new Set(substring)`: This also takes `O(K)` time.
        3.  `map.set(substring, ...)`: Hashing a string of length `K` also takes `O(K)` time.
      * So, the loop is `O(N * K)`.
  * **The "Trick":** The constraints state `minSize <= 26`. Because `K` is bounded by a small constant, `O(N * K)` is effectively **`O(N)`**\!
  * **Your Code's Sort:** `O(M log M)`
      * `M` is `map.size`, which in the worst case could be `O(N)`.
      * This means your sort is `O(N log N)`.
  * **Conclusion:** Your `for` loop is already `O(N)`, which is optimal. The **real** bottleneck, as you correctly suspected, was the `sort`\! By replacing the `O(N log N)` sort with an `O(N)` pass, you make the whole algorithm truly `O(N)`.

-----

### \#\# ✅ Final Optimal Code

Here is your own code, modified with the optimal `O(N)` method to find the max frequency.

```typescript
function maxFreq(s: string, maxLetters: number, minSize: number, maxSize: number): number {
    // The maxSize is irrelevant, as the max frequency will always
    // be found with a substring of length minSize.
    
    // map stores [substring -> frequency]
    const map = new Map<string, number>();
    let maxFrequency = 0;
    
    // O(N) loop (since minSize <= 26)
    for(let i = 0; i < s.length - minSize + 1; i++){
        const substring = s.substring(i, i + minSize);
        
        // This check can be optimized by maintaining a sliding window
        // of character counts, but given minSize <= 26, this is fast.
        if(new Set(substring).size <= maxLetters){
            const newCount = (map.get(substring) || 0) + 1;
            map.set(substring, newCount);
            
            // We can track the max frequency *as we go*
            // This avoids a second pass entirely!
            if (newCount > maxFrequency) {
                maxFrequency = newCount;
            }
        }
    }

    return maxFrequency;
};
```

*Note: I've made one more optimization. You don't even need a second pass at all\! You can track the `maxFrequency` inside the first loop, making the whole thing a single, clean `O(N)` pass.*