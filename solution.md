1309. Decrypt String from Alphabet to Integer Mapping

Easy
String


-----

## Real-World Analogy

Think of this like translating Morse code, but with two different dot/dash patterns.

  * Short patterns (`1` to `9`) mean one thing.
  * Longer patterns (`10#` to `26#`) mean another.

Your code is like having a lookup book (the `map`) but you only wrote down the short patterns. When you see a long pattern, you try to look up part of it (`"10"`) in the short-pattern section, which doesn't work.

The better way is to just know the rules directly: "If I see a `#` two spots ahead, read two digits and translate *that* number. Otherwise, read one digit and translate *that* number."

-----

## 中文思路分析 (Chinese Thought Process)

#### \#\#\#\# Code Review & Debugging

1.  **Map 建立錯誤:** 你的 `map` 只儲存了 `{"1": "a", "2": "b", ..., "9": "i"}`。當你遇到 `"10#"` 時，你嘗試查詢 `map.get("10")`，但這個鍵並不存在於你的 Map 中。
2.  **可以直接計算:** 我們其實不需要 Map。數字和字母之間有一個直接的數學關係。字母 'a' 對應數字 1，'b' 對應 2，依此類推。我們可以利用 ASCII/Unicode 碼來轉換。`'a'.charCodeAt(0)` 給出 'a' 的碼點，那麼數字 `n` 對應的字母就是 `String.fromCharCode('a'.charCodeAt(0) + n - 1)`。

#### \#\#\#\# The Optimal Strategy: Direct Calculation

我們可以保留你的 `while` 迴圈結構，但在找到數字後直接計算對應的字母。

**Algorithm:**

1.  初始化 `output = ""`，`i = 0`。
2.  使用 `while (i < s.length)` 迴圈遍歷字串。
3.  **檢查 `#`:** `if (i + 2 < s.length && s[i + 2] === '#')`
      * 如果是，解析這兩位數字：`num = parseInt(s.substring(i, i + 2))`。
      * 計算對應字母：`char = String.fromCharCode('a'.charCodeAt(0) + num - 1)`。
      * 將 `char` 加入 `output`。
      * `i += 3`。
4.  **否則 (處理單位數):**
      * 解析這位數字：`num = parseInt(s[i])`。
      * 計算對應字母：`char = String.fromCharCode('a'.charCodeAt(0) + num - 1)`。
      * 將 `char` 加入 `output`。
      * `i++`。
5.  返回 `output`。

-----

## Complexity Analysis & Optimization

  * **Your Solution (Corrected or Direct Calculation):**

      * **Time Complexity: O(N)**, where N is the length of `s`. We make a single pass through the string. Operations like `substring`, `parseInt`, and `fromCharCode` are very fast.
      * **Space Complexity: O(N)** for the `output` string. Auxiliary space is **O(1)** as we only use a few variables.

  * **Optimization Suggestions:**

      * **The direct calculation method is optimal.** It avoids the overhead of creating and looking up in a map while maintaining the best possible time and space complexity. Your iteration strategy was already perfect for this.

-----

## English Explanation & Final Code

#### \#\#\#\# Code Review & Debugging

1.  **Map Creation Error:** Your `map` only contains keys "1" through "9". When you encounter "10\#", your code tries `map.get("10")`, which doesn't exist.
2.  **Direct Calculation is Simpler:** We don't actually need the map. There's a direct mathematical relationship between the numbers (1-26) and the letters ('a'-'z'). We can use character codes: `String.fromCharCode('a'.charCodeAt(0) + number - 1)` gives the correct letter for a given `number`.

#### \#\#\#\# The Optimal Strategy: Direct Calculation

Keep your `while` loop structure, but calculate the character directly.

**Algorithm:**

1.  Initialize `output = ""`, `i = 0`.
2.  Loop while `i < s.length`.
3.  **Check for `#`:** `if (i + 2 < s.length && s[i + 2] === '#')`
      * If yes, parse the 2-digit number: `num = parseInt(s.substring(i, i + 2))`.
      * Get the character: `char = String.fromCharCode('a'.charCodeAt(0) + num - 1)`.
      * Append `char` to `output`.
      * Increment `i` by 3.
4.  **Else (handle single digit):**
      * Parse the 1-digit number: `num = parseInt(s[i])`.
      * Get the character: `char = String.fromCharCode('a'.charCodeAt(0) + num - 1)`.
      * Append `char` to `output`.
      * Increment `i` by 1.
5.  Return `output`.

### \#\# Final Code (Direct Calculation)

```typescript
function freqAlphabets(s: string): string {
    let output = "";
    let i = 0;
    const baseCharCode = 'a'.charCodeAt(0);

    while (i < s.length) {
        // Look ahead to check for the '#' indicating a two-digit code
        if (i + 2 < s.length && s[i + 2] === '#') {
            // Parse the two-digit number
            const num = parseInt(s.substring(i, i + 2));
            // Calculate and append the corresponding character
            output += String.fromCharCode(baseCharCode + num - 1);
            // Move the pointer past the number and the '#'
            i += 3;
        } else {
            // Parse the single-digit number
            const num = parseInt(s[i]);
            // Calculate and append the corresponding character
            output += String.fromCharCode(baseCharCode + num - 1);
            // Move the pointer to the next character
            i++;
        }
    }

    return output;
}

// Example 1 Test
console.log(`Testing "10#11#12": "${freqAlphabets("10#11#12")}"`); // Expected: "jkab"

// Example 2 Test
console.log(`Testing "1326#": "${freqAlphabets("1326#")}"`); // Expected: "acz"
```