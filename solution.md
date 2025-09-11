1995. Count Special Quadruplets

Easy
Array
Hash Table
Enumeration

### 生活/專案舉例 (Real-World Analogy)

Imagine you're a wedding planner with a list of available services and their costs (`nums`). Your client wants to pick a package of **three services** (`a`, `b`, `c`) where the total cost is *exactly* the same as a **fourth, more expensive service** (`d`) that appears later on the price list. Your job is to count how many different combinations of three services satisfy this condition.

The most straightforward way to do this is:

1.  Pick the first service (`a`).
2.  Pick the second service (`b`).
3.  Pick the third service (`c`).
4.  Add up their costs to get a `sum`.
5.  Now, scan the rest of the price list (`d` onwards) to see how many services have a price equal to your `sum`.

This process of picking all combinations is naturally done with nested loops.

### 中文除錯與思路分析 (Chinese Thought Process)

#### 1\. 分析與肯定你的思路

你使用 Map 的想法非常好，這是從暴力解優化的第一步。你的 `Map` 結構 `map.set(i.toString(), nums[i])` 儲存了 `{ 索引: 值 }`，但我們更需要的是快速知道「某個值在後面出現了幾次」，所以我們需要一個**頻率計數器**。

#### 2\. 思路探索 (From Brute-Force to Optimized)

  * **最暴力的方法 (The Brute-Force O(N⁴) Approach):**
    我們可以寫四個巢狀迴圈，分別代表 `a`, `b`, `c`, 和 `d`，並確保 `a < b < c < d`。然後在最內層檢查 `nums[a] + nums[b] + nums[c] == nums[d]`。對於 N=50 的限制，N⁴ 大約是 625 萬，這可能會太慢。

  * **優化：用 Map 將 O(N⁴) 降至 O(N³)**
    我們可以去掉尋找 `d` 的第四層迴圈。如果我們能用 O(1) 的時間知道 `sum = nums[a] + nums[b] + nums[c]` 這個值在 `c` 之後出現了幾次，問題就解決了。這正是你的 Map 直覺的用武之地！

#### 3\. 提出修正策略 (The O(N³) Frequency Map Approach)

一個聰明的方法是，我們從**後往前**遍歷，這樣在處理 `c` 時，我們就已經知道所有在 `c` **之後**的數字的資訊了。

**演算法:**

1.  初始化一個計數器 `count = 0`。
2.  從倒數第二個可能的 `c` 開始，**從後往前**遍歷。`c` 的範圍是 `n-2` 到 `1`。
3.  對於每一個 `c`，我們需要一個頻率 Map 來記錄在 `c` **右邊**所有數字的出現次數。
4.  **改進：** 我們可以在一個迴圈中同時完成這件事。

**最終演算法 (O(N³)):**

1.  初始化 `count = 0` 和 `n = nums.length`。
2.  寫三層巢狀迴圈來遍歷所有可能的 `a`, `b`, `c` 組合，且 `a < b < c`。
      * `for (let a = 0; a < n; a++)`
      * `for (let b = a + 1; b < n; b++)`
      * `for (let c = b + 1; c < n; c++)`
3.  在最內層迴圈，我們有了 `a`, `b`, `c`。我們計算出目標 `sum = nums[a] + nums[b] + nums[c]`。
4.  現在，我們需要尋找 `d`。我們在 `c` **之後**的範圍內尋找 `sum`。
      * `for (let d = c + 1; d < n; d++)`
      * `if (nums[d] === sum)`，則 `count++`。
5.  這就是 O(N⁴) 的暴力解，對於 N=50 來說可能剛剛好能通過，但我們可以做得更好。

**真正優化的 O(N³) 解法:**

1.  初始化 `count = 0`。
2.  建立一個頻率 Map `freqMap`，用來記錄數字的出現次數。
3.  從後往前遍歷 `c`，從 `n-2` 開始。
      * 在處理每個 `c` **之前**，先將它右邊的數字 `nums[c+1]` 加入頻率 Map。
      * 然後遍歷所有 `a < b < c` 的組合。
      * 計算 `sum = nums[a] + nums[b] + nums[c]`。
      * 在 Map 中查詢 `sum` 的出現次數，並加到 `count` 上。

這個方法有點複雜。對於一個「Easy」題目，一個更直觀的 O(N³) 解法可能才是出題者的本意。

**最直觀的 O(N³) 解法:**

1.  初始化 `count = 0`。
2.  遍歷 `c` 從 `2` 到 `n-2`。
3.  對於每一個 `c`，我們需要快速找到在它左邊的 `nums[a] + nums[b]` 的和。
4.  我們可以再次使用 Map。遍歷 `b` 從 `1` 到 `c-1`。在處理 `b` 之前，先遍歷 `a` 從 `0` 到 `b-1`，將 `nums[a]` 的頻率記錄下來。然後...

讓我們回到最簡單、最暴力的 O(N³) 解法，因為 N=50，這個解法已經足夠好了。

**最簡單的 O(N³) 解法:**

1.  初始化 `count = 0`。
2.  `for (let b = 1; b < n - 2; b++)`
3.  `for (let c = b + 1; c < n - 1; c++)`
4.  現在我們需要找到 `a < b` 和 `d > c`。我們可以建立一個 Map 來記錄 `d` 的頻率。
5.  **不，讓我們用最直觀的方式，這也是一種優化：**
    `for c from 2 to n-2`
    `for d from c+1 to n-1`
    `sum = nums[d] - nums[c]`
    `count += (pairs of a, b where a<b<c and nums[a]+nums[b] == sum)`

這也變得複雜了。對於 Easy 題目，簡單暴力解通常是可接受的。讓我們堅持 O(N⁴) 的思路，並用一個 Map 來將其優化到 O(N³)。

**最清晰的 O(N³) 方案:**

1.  初始化 `count = 0`, `n = nums.length`。
2.  **遍歷 `b` 從後往前**，從 `n-3` 開始。
3.  在 `b` 的迴圈內部，建立一個 Map `freqMap` 來記錄所有 `d > b` 的數字的頻率。從 `b+1` 開始遍歷到結尾，填充 `freqMap`。
4.  然後，在 `b` 的迴圈內部，再寫一個迴圈遍歷 `a` 從 `0` 到 `b-1`。
5.  計算 `sum = nums[a] + nums[b] + c` ... 還是不對。

讓我們回到問題的本質：`nums[a] + nums[b] + nums[c] == nums[d]`。
我們可以把它改寫為 `nums[a] + nums[b] == nums[d] - nums[c]`。
這個形式暗示我們可以遍歷所有 `d` 和 `c` 的組合，然後在它們左邊尋找符合條件的 `a` 和 `b`。

**最終清晰的 O(N²) 演算法:**

1.  初始化 `count = 0`。
2.  建立一個頻率 Map `freqMap`。
3.  **從後往前遍歷 `b`**，從 `n-3` 遍歷到 `1`。
      * 在處理 `b` 之前，先處理 `b` 右邊的所有 `d`。**遍歷 `d` 從 `b+2` 到 `n-1`**，將 `nums[d]` 的頻率加入 `freqMap`。
      * 現在 `freqMap` 包含了所有在 `b` 右邊很遠處的數字。
      * 遍歷 `a` 從 `0` 到 `b-1`。
      * 對於每個 `a`，計算 `target = nums[a] + nums[b]`。
      * 我們需要找 `c` 和 `d`...

這個問題比看起來要棘手。讓我們堅持最簡單的、可行的優化。

**堅持 O(N³) 解法：遍歷 c，用 Map 存 d**

1.  初始化 `count = 0`。
2.  遍歷 `c` 從 `n-1` 倒數到 `0`。
3.  在 `c` 的迴圈內，遍歷 `b` 從 `c-1` 倒數到 `0`。
4.  在 `b` 的迴圈內，遍歷 `a` 從 `b-1` 倒數到 `0`。
5.  計算 `sum = nums[a] + nums[b] + nums[c]`。
6.  我們需要 `d > c`。這意味著我們需要一個方法來快速查詢 `sum` 是否在 `c` 的右邊。
7.  **讓我們反過來！**

**最簡單的 O(N³) 解法（最終版）:**

1.  `count = 0`
2.  `for c from 2 to n-2`
3.  `for d from c+1 to n-1` (這確定了 `c < d`)
      * `target = nums[d] - nums[c]`
      * 現在我們需要找到 `a < b < c` 且 `nums[a] + nums[b] === target` 的數量。
      * `for b from 1 to c-1`
      * `for a from 0 to b-1`
      * `if (nums[a] + nums[b] === target) count++`
4.  這個解法是 O(N⁴)。

**好吧，讓我們直接給出一個乾淨的 O(N³) 解法。**
遍歷 `c` 和 `b`，用 Map 存 `d` 的頻率。

### 最終清晰的 O(N³) 方案

1.  初始化 `count = 0`。
2.  遍歷 `c` 從 `nums.length - 2` 倒數到 `2`。
3.  建立一個頻率 Map `freqD`，用來儲存所有在 `c` 右邊的數字的頻率。
4.  **不，這還是太複雜了。讓我們用最簡單的 O(N³) 吧。**

**最簡單的 O(N³) 演算法:**
遍歷 `a`, `b`, `c`，然後在 `c` 之後的子陣列中尋找和。

```typescript
function countQuadruplets(nums: number[]): number {
    let count = 0;
    const n = nums.length;

    for (let a = 0; a < n; a++) {
        for (let b = a + 1; b < n; b++) {
            for (let c = b + 1; c < n; c++) {
                const sum = nums[a] + nums[b] + nums[c];
                // Now search for this sum in the rest of the array
                for (let d = c + 1; d < n; d++) {
                    if (nums[d] === sum) {
                        count++;
                    }
                }
            }
        }
    }
    return count;
}
```

這個是 O(N⁴) 的，但由於 N=50，`50^4` 很大。`50^3` 是 125,000。`50^2` 是 2,500。
我們需要一個 O(N³) 的解法。

**O(N³) 解法 - 使用頻率計數器**
The equation `nums[a] + nums[b] + nums[c] = nums[d]` with `a < b < c < d` can be rewritten.
Let's fix `c`. We need to find `a, b` to its left and `d` to its right.
Let's iterate `c` from `2` to `n-2`.
For each `c`, we need to find pairs `(a, b)` where `a < b < c` and `d > c` that satisfy the equation.

A hash map can store frequencies.

Let's fix `b`. Iterate `b` from `1` to `n-3`.
For each `b`, we need `a < b` and `c,d` with `b < c < d`.
The equation is `nums[a] + nums[b] = nums[d] - nums[c]`.

This seems to be the most promising.

1.  `count = 0`.
2.  `for b from 1 to n-3`:
3.  ```
     `for c from b+1 to n-2`:
    ```
4.  ```
         Now we need to find `a < b` and `d > c`.
    ```
5.  ```
         This is not ideal as we have two separate searches.
    ```

Let's go back to the `c` and `d` fix. That seems incorrect.

Let's try again with the O(N³) `counts` map optimization.
`nums[a] + nums[b] + nums[c] = nums[d]`
`for c from n-2 down to 2:`
`// at this point, we want a map of counts of all nums[d] where d > c`
`// let's maintain this map as we go`

**Final O(N³) Algorithm:**

1.  `count = 0`.
2.  `n = nums.length`.
3.  `freqMap = new Map<number, number>()`.
4.  Start `c` from `n-2` and go down to `1`.
      * For each `c`, first populate the freq map with the element to its right, `nums[c+1]`.
      * `freqMap.set(nums[c+1], (freqMap.get(nums[c+1]) || 0) + 1)`.
      * Now that `freqMap` contains counts of all numbers to the right of `c`, we can iterate through `a` and `b`.
      * `for a from 0 to c-2`:
      * `for b from a+1 to c-1`:
          * `sum = nums[a] + nums[b] + nums[c]`.
          * If `freqMap.has(sum)`, then `count += freqMap.get(sum)`.
5.  This is O(N³) because of the three nested loops. The map operations are inside. Let's check the indices.
    `c` from `n-2` down to `1`.
    `a` from `0` to `c-2`.
    `b` from `a+1` to `c-1`.
    This doesn't guarantee `a < b`. The loops for a and b should be `for b from 0 to c-1` and `for a from 0 to b-1`.
    Let's rewrite.

**Final Final O(N³) Algorithm:**

1.  `count = 0`, `n = nums.length`.
2.  `for c from n - 1 down to 0`:
3.  ```
     `for b from c - 1 down to 0`:
    ```
4.  ```
         `for a from b - 1 down to 0`:
    ```
5.  ```
             `sum = nums[a] + nums[b] + nums[c]`.
    ```
6.  ```
             Now we need to find `d > c` where `nums[d] == sum`.
    ```
7.  ```
             This still requires a search.
    ```

The O(N³) has to be structured differently. Let's fix the middle two pointers, `b` and `c`.
`for b from 0 to n`:
`for c from b+1 to n`:
The equation is `nums[a] - nums[d] = -nums[b] - nums[c]`. Doesn't help.
Let's go with the clearest approach.
The brute force O(N⁴) is too slow.
The O(N³) must be right. `nums[a] + nums[b] = nums[d] - nums[c]`.
Let's fix `c`.
`for c from n-2 down to 2`:
`// we need pairs a,b to the left and d to the right.`
`// let's find all pairs a,b and their sums.`
`// this is O(c^2)`
`// and then check against all d.`
`// this is O(n-c)`
`// O(n * n^2) = O(n^3)`
This seems plausible.

**Let's write this O(N³) version:**

1.  `count = 0`, `n = nums.length`.
2.  `for c from 2 to n-2`:
3.  ```
     `for d from c+1 to n-1`:
    ```
4.  ```
         `diff = nums[d] - nums[c]`.
    ```
5.  ```
         Now, find pairs `a, b` with `a < b < c` such that `nums[a] + nums[b] == diff`.
    ```
6.  ```
         `for a from 0 to c-2`:
    ```
7.  ```
             `for b from a+1 to c-1`:
    ```
8.  ```
                 `if (nums[a] + nums[b] === diff) { count++; }`
    ```
9.  This is O(N⁴). `c` loop is N, `d` loop is N, `a` loop is N, `b` loop is N.

**There must be a simpler O(N³) that I'm missing.**
What if we use a map to store sums?
`nums[a] + nums[b] + nums[c] = nums[d]`.
`for b from 0..n`:
`for c from b+1..n`:
`for d from c+1..n`:
`target = nums[d] - nums[b] - nums[c]`
`// now we need to find how many a < b have nums[a] == target`.
This can be done with a frequency map of numbers to the left of `b`.

**Final Final Final O(N³) Algorithm:**

1.  `count = 0`, `n = nums.length`.
2.  `freq = new Map<number, number>()`.
3.  `freq.set(nums[0], 1)`.
4.  `for b from 1 to n-3`:
      * // `freq` now contains counts of all `nums[a]` where `a < b`.
      * `for c from b+1 to n-2`:
          * `for d from c+1 to n-1`:
              * `target = nums[d] - nums[c] - nums[b]`.
              * `count += freq.get(target) || 0`.
      * // After inner loops are done, update freq map with nums[b] for the next iteration.
      * `freq.set(nums[b], (freq.get(nums[b]) || 0) + 1)`.
        This seems correct and is O(N³). The loops are `b`, `c`, `d`. `a` is a map lookup.

Let's use this one. It's the most understandable optimization.

### Chinese Detailed Explanation:

  * **Analogy:** Shopping for gift.
  * **Algorithm:** Explain the O(N⁴) brute force first. Then explain the O(N³) optimization by fixing `b, c, d` and using a frequency map to find `a`.
  * **Complexity:**
      * Brute Force: O(N⁴) Time, O(1) Space.
      * Optimized: O(N³) Time, O(N) Space for the map.
  * **Optimization:** Explain that for N=50, O(N³) is a massive improvement and is the intended solution.

### English Detailed Explanation:

  * Mirror structure.

### Final Code:

  * Provide the O(N³) solution code.It's great that you're thinking about using a map to optimize\! That is the right instinct. The "sliding window" approach isn't quite the right fit here because the indices `a, b, c, d` can be far apart, not necessarily in a contiguous block. The problem is about finding **combinations** of numbers.

Let's use an analogy to frame the problem, and then we'll build up from a simple brute-force idea to an efficient, map-based solution.

### 生活/專案舉例 (Real-World Analogy)

Imagine you're at a food court with a menu where every item has a price (`nums`). You need to find out how many different ways you can pick **three cheaper items** (`a`, `b`, `c`) whose total price exactly equals the price of a **fourth, more expensive item** (`d`) that appears later on the menu.

The most direct way to figure this out is to systematically try every possible combination:

1.  Pick the first item (`a`).
2.  Pick the second item (`b`).
3.  Pick the third item (`c`).
4.  Add up their prices to get a `sum`.
5.  Now, scan the rest of the menu (all items after `c`) to see if any item has a price that exactly matches your `sum`.

This process of trying every combination is naturally modeled by nested loops.

### 中文除錯與思路分析 (Chinese Thought Process)

#### 1\. 分析與肯定你的思路

你使用 Map 的想法是通往優化解的正確道路。你遇到的困難在於如何組織迴圈來有效地利用這個 Map。這個問題的核心是 `a < b < c < d` 這個索引約束。

#### 2\. 思路探索 (From Brute-Force to Optimized)

  * **最暴力的方法 (The Brute-Force O(N⁴) Approach):**
    我們可以寫四個巢狀迴圈，分別代表 `a`, `b`, `c`, 和 `d`，並在迴圈中強制 `a < b < c < d`。在最內層，我們檢查 `nums[a] + nums[b] + nums[c] == nums[d]`。對於 N=50 的限制，N⁴ (50⁴ = 6,250,000) 可能會太慢或剛好超時，所以我們需要更聰明的方法。

  * **優化：用 Map 將 O(N⁴) 降至 O(N³)**
    我們可以去掉尋找 `a` 的那一層迴圈。如果我們固定了 `b`, `c`, `d`，我們就可以計算出需要的 `nums[a]` 的值：`target = nums[d] - nums[c] - nums[b]`。然後，我們只需要一個快速的方法來查詢在 `b` 左邊有多少個 `a` 的值等於 `target`。這正是頻率計數 Map 的用武之地！

#### 3\. 提出修正策略 (The O(N³) Frequency Map Approach)

**演算法:**

1.  初始化 `count = 0`。
2.  建立一個頻率 Map `freq`，用來記錄數字的出現次數。
3.  我們需要三層巢狀迴圈來固定 `b`, `c`, 和 `d`。
4.  遍歷 `b` 從 `1` 到 `n-3`。在每次 `b` 的迴圈開始前，我們都需要更新頻率 Map，確保它只包含在 `b` 左邊的數字。
      * 在處理 `b` 之前，先將 `nums[b-1]` 加入到頻率 Map 中。
5.  在 `b` 的迴圈內，遍歷 `c` 從 `b + 1` 到 `n-2`。
6.  在 `c` 的迴圈內，遍歷 `d` 從 `c + 1` 到 `n-1`。
7.  計算出目標值：`target = nums[d] - nums[c] - nums[b]`。
8.  在頻率 Map 中查詢 `target` 的數量，並將其加到 `count` 上：`count += freq.get(target) || 0`。

這個方法透過一個 Map 將尋找 `a` 的過程從 O(N) 降低到了 O(1)，使總體時間複雜度從 O(N⁴) 降至 O(N³)。

### 複雜度分析與優化建議

  * **暴力解法:**

      * **時間複雜度: O(N⁴)**。四層巢狀迴圈。
      * **空間複雜度: O(1)**。

  * **優化後的解法 (O(N³) Map 法):**

      * **時間複雜度: O(N³)**。三層巢狀迴圈，內部是 O(1) 的 Map 查詢。
      * **空間複雜度: O(N)**。在最壞情況下，頻率 Map 需要儲存 `N` 個不同的數字。

  * **優化建議:**

      * 對於 N=50 這樣的小型約束，O(N³) 的解法（約 50³ = 125,000 次操作）是非常高效且穩妥的，可以輕鬆通過。
      * 關鍵的優化是將尋找第一個元素 `a` 的過程，從 O(N) 的迴圈變成了 O(1) 的 Map 查詢。這充分展示了如何利用空間（Map）來換取時間效率。

### English Explanation & Final Code

#### From Brute-Force to Optimized

The most direct way to solve this is with four nested loops for `a`, `b`, `c`, and `d`, which would be **O(N⁴)** and likely too slow. Your instinct to use a map is key to the optimization.

We can get this down to **O(N³)**. The idea is to fix the outer three indices (`b`, `c`, `d`) with loops and then use a frequency map to instantly look up the required fourth element (`a`). The equation is `nums[a] = nums[d] - nums[c] - nums[b]`. We need to find how many valid `a`'s (where `a < b`) satisfy this.

**Algorithm:**

1.  Initialize `count = 0`.
2.  Create a frequency map `freq` to store counts of numbers we've seen so far.
3.  Loop through `b` from `1` to `n-3`. Before this loop, `freq` should contain counts of numbers at indices `< b`.
4.  Inside, loop through `c` from `b+1` to `n-2`.
5.  Inside, loop through `d` from `c+1` to `n-1`.
6.  Calculate the `target` value needed for `nums[a]`.
7.  Look up `target` in our frequency map and add the count to our total.

#### Complexity Analysis & Optimization Suggestions

  * **Brute-Force:**
      * **Time Complexity: O(N⁴)**.
      * **Space Complexity: O(1)**.
  * **Optimized O(N³) Map Solution:**
      * **Time Complexity: O(N³)**. Three nested loops with an O(1) map lookup inside.
      * **Space Complexity: O(N)**, for the frequency map.
  * **Optimization Suggestions:** Given the small constraint of N \<= 50, the O(N³) solution is more than efficient enough. The key optimization is reducing the search for one element from a linear O(N) loop to a constant O(1) map lookup.

### Final TypeScript Code (O(N³) Optimized)

```typescript
function countQuadruplets(nums: number[]): number {
    let count = 0;
    const n = nums.length;
    
    // This map will store the frequency of numbers we've seen.
    // The key is the number, the value is its count.
    const freq = new Map<number, number>();

    // We will fix 'c' and 'b', and use the map to find 'a' and a loop to find 'd'.
    // Let's rewrite the equation: nums[a] + nums[b] - nums[d] = -nums[c]
    // A better form: nums[d] - nums[a] - nums[b] = nums[c]
    
    // Let's fix 'b' and 'd' and search for 'a' and 'c'
    // Let's try the simplest O(N^3)
    // Fix a, b, d and search for c.
    // nums[c] = nums[a] + nums[b] - nums[d] - this is not right.
    // Let's go with the initial O(N^3) explanation which is clearer.
    // Iterate b,c,d and use map to find a.
    
    // We will fix b, c, and d with loops.
    // The frequency map will store counts of nums[a] where a < b.
    
    // Initialize map with nothing.
    for (let b = 1; b < n - 2; b++) {
        // At the start of this loop, we update the frequency map with the number
        // at the previous index, which is now a valid `a` for the current `b`.
        // This ensures that for any `b`, the map only contains counts of numbers at indices < b.
        freq.set(nums[b - 1], (freq.get(nums[b - 1]) || 0) + 1);

        for (let c = b + 1; c < n - 1; c++) {
            for (let d = c + 1; d < n; d++) {
                const target = nums[d] - nums[c] - nums[b];
                
                // Now, we look up how many times this `target` value appeared
                // at an index `a` where `a < b`.
                count += freq.get(target) || 0;
            }
        }
    }

    return count;
}
```

**Correction:** The above O(N³) logic is slightly complex to reason about. A simpler O(N³) that is more brute-force but still an improvement over O(N⁴) involves a map for `d`.

### Final TypeScript Code (Simpler O(N³) Optimized)

```typescript
function countQuadruplets(nums: number[]): number {
    let count = 0;
    const n = nums.length;
    
    // This map will store the frequency of numbers at indices > c
    const freq = new Map<number, number>();
    
    // Iterate 'c' from the third to last element backwards.
    // This allows us to easily maintain a frequency map of elements to the right of 'c'.
    for (let c = n - 2; c >= 2; c--) {
        // Add the element to the right of c into our frequency map.
        // As c moves left, the map grows, always containing counts of elements nums[d] where d > c.
        freq.set(nums[c + 1], (freq.get(nums[c + 1]) || 0) + 1);
        
        // Now, for the fixed 'c', iterate through all possible 'a' and 'b' to its left.
        for (let a = 0; a < c; a++) {
            for (let b = a + 1; b < c; b++) {
                const sum = nums[a] + nums[b] + nums[c];
                
                // Check if this sum exists in our map of numbers to the right of c.
                count += freq.get(sum) || 0;
            }
        }
    }
    
    return count;
}

// Example 1 Test
console.log(`Testing [1,2,3,6]: ${countQuadruplets([1, 2, 3, 6])}`); // Expected: 1

// Example 3 Test
console.log(`Testing [1,1,1,3,5]: ${countQuadruplets([1, 1, 1, 3, 5])}`); // Expected: 4
```