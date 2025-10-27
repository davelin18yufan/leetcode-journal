## 📚 Problems by Category

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|
| 108 | [Convert Sorted Array to Binary Search Tree](./problems/108-convert-sorted-array-to-binary-search-tree.md) | Easy | Divide and Conquer, Recursion | Creating a fair tournament bracket. | 🚧 WIP. Optimal solution uses pointers, not slicing. |
| 561 | [Array Partition](./problems/561-array-partition.md) | Easy | Greedy, Sorting | Maximizing dance competition scores. | Sort the array and sum every second element. |
| 1337 | [The K Weakest Rows in a Matrix](./problems/1337-the-k-weakest-rows-in-a-matrix.md) | Easy | Binary Search, Sorting | Ranking teams in a tournament. | O(M log N + M log M) solution using binary search for counting and then sorting. |
| 1800 | [Maximum Ascending Subarray Sum](./problems/1800-maximum-ascending-subarray-sum.md) | Easy | Single Pass, Greedy | Analyzing stock price trends. | Optimal O(N) time and O(1) space by tracking current and max sums. |
| 1380 | [Lucky Numbers in a Matrix](./problems/1380-lucky-numbers-in-a-matrix.md) | Easy | Matrix, Preprocessing | Finding a topographical "saddle point". | O(M*N) solution by finding the intersection of row minimums and column maximums. |
| 1995 | [Count Special Quadruplets](./problems/1995-count-special-quadruplets.md) | Easy | Hash Table, O(N³) | Counting specific combinations in a dataset. | A good example of trading space for time (O(N) space for O(N³) time). |
| 2255 | [Count Prefixes of a Given String](./problems/2255-count-prefixes-of-a-given-string.md) | Easy | String Manipulation, Iteration | Autocomplete suggestions. | Optimal O(N*M) solution using `startsWith`. |
| 2006 | [Count Number of Pairs With Absolute Difference K](./problems/2006-count-number-of-pairs-with-absolute-difference-k.md) | Easy | Hash Map | Customer Data Analysis | Use a hash map to track frequencies for O(1) lookups. |
| 2744 | [Find Maximum Number of String Pairs](./problems/2744-find-maximum-number-of-string-pairs.md) | Easy | Hash Table, Simulation | Pairing socks from a pile of laundry. | Use a Set to track seen words and find pairs. |
| 724 | [Find Pivot Index](./problems/724-find-pivot-index.md) | Easy | Prefix Sum | Balancing a seesaw. | O(N) time, O(1) space using total sum. |
| 2446 | [Determine if Two Events Have Conflict](./problems/2446-determine-if-two-events-have-conflict.md) | Easy | Direct String Comparison | Yes | Compare time strings directly to check for overlap. |
| 867 | [Transpose Matrix](./problems/867-transpose-matrix.md) | Easy | Matrix Transposition | Rotating a spreadsheet | Create a new matrix with swapped dimensions and copy elements. |

### Array Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---|---|---|---|---|
| 1732 | [Find the Highest Altitude](./problems/1732-find-the-highest-altitude.md) | Easy | Prefix Sum | Tracking your bank account balance | Iterate through gains, tracking current and max altitude. |
| 2012 | [Sum of Beauty in the Array](./problems/2012-sum-of-beauty-in-the-array.md) | Medium | Prefix Sum, Suffix Min | Mountain range peak finding | Marked as incomplete for future review. |
| 1706 | [Where Will the Ball Fall](./problems/1706-where-will-the-ball-fall.md) | Medium | Direct Simulation | Pachinko machine simulation | Clean simulation is key. |
| 3684 | [Maximize Sum of At Most K Distinct Elements](./problems/3684-maximize-sum-of-at-most-k-distinct-elements.md) | Easy | Greedy, Sorting | Packing a treasure chest. | Greedy: get unique elements with Set, sort descending, take top k. |
|---|---|---|---|---|---|
| 2859 | [Sum of Values at Indices With K Set Bits](./problems/2859-sum-of-values-at-indices-with-k-set-bits.md) | Easy | Bit Manipulation | Quality control inspector analogy. | Use bit manipulation to count set bits in an index `i`. |
|---|---------|------------|--------------|-------------------|-------|
| 908 | [Smallest Range I](./problems/908-smallest-range-i.md) | Easy | Math | Adjusting building temperatures | The key is to only consider the min and max values. |
| 303 | [Range Sum Query - Immutable](./problems/303-range-sum-query-immutable.md) | Easy | Prefix Sum, O(1) Query | Road trip mileage log | Pre-computation for fast queries. |
| 2828 | [Check if a String Is an Acronym of Words](./problems/2828-check-if-a-string-is-an-acronym-of-words.md) | Easy | First Character Matching | Acronym Verification | Compare first char of each word. |
| 2563 | [Count the Number of Fair Pairs](./problems/2563-count-the-number-of-fair-pairs.md) | Medium | Two Pointers, Sorting | Finding dance partners. | O(N log N) solution by sorting and using two pointers. |
| 825 | [Friends Of Appropriate Ages](./problems/825-friends-of-appropriate-ages.md) | Medium | Two Pointers, Sorting | Analyzing demographics at a large convention. | O(N) solution using age counting. |
| 3355 | [Zero Array Transformation I](./problems/3355-zero-array-transformation-i.md) | Medium | Prefix Sum | Calculating total coverage of overlapping intervals. | Use a difference array to track changes, then calculate prefix sum. |

### String Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|
| 3216 | [Lexicographically Smallest String After a Swap](./problems/3216-lexicographically-smallest-string-after-a-swap.md) | Easy | Greedy | Optimizing a sequence with a single swap. | The first beneficial swap is always the best one. |
| 2255 | [Count Prefixes of a Given String](./problems/2255-count-prefixes-of-a-given-string.md) | Easy | Iteration, `startsWith` | Autocomplete suggestions. | Optimal O(N*M) solution for single-pass check. |
| 3146 | [Permutation Difference between Two Strings](./problems/3146-permutation-difference-between-two-strings.md) | Easy | Hash Table, Two-Pass | Calculating a "shuffling score" in a race. | Optimal O(N) time and O(K) space solution. |
| 1678 | [Goal Parser Interpretation](./problems/1678-goal-parser-interpretation.md) | Easy | String Manipulation, Look-Ahead | Telegraph operator decoding messages | Replace `()` with `o` and `(al)` with `al`. |
| 3407 | [Substring Matching Pattern](./problems/3407-substring-matching-pattern.md) | Medium | String Splitting | Wildcard pattern matching | Split by wildcard, check prefix/suffix |
| 387 | [First Unique Character in a String](./problems/387-first-unique-character-in-a-string.md) | Easy | Two-Pass Hash Map | Data stream analysis | O(N) time, O(1) space for alphabet |
| 2810 | [Faulty Keyboard](./problems/2810-faulty-keyboard.md) | Easy | Simulation, Array | Text editor simulation | Use mutable array to build string |
| 3110 | [Score of a String](./problems/3110-score-of-a-string.md) | Easy | String Manipulation | Hiking elevation change analogy | O(N) time, O(1) space single-pass |
| 2446 | [Determine if Two Events Have Conflict](./problems/2446-determine-if-two-events-have-conflict.md) | Easy | Direct String Comparison | Yes | Compare time strings directly to check for overlap. |
| 434 | [Number of Segments in a String](./problems/434-number-of-segments-in-a-string.md) | Easy | Single Pass | String | Counting cars in a freight train. |
| 1021 | [Remove Outermost Parentheses](./problems/1021-remove-outermost-parentheses.md) | Easy | Depth Counter | Parentheses Parsing | Use a counter to track nesting depth. |
| 2828 | [Check if a String Is an Acronym of Words](./problems/2828-check-if-a-string-is-an-acronym-of-words.md) | Easy | Character-by-Character Comparison | Acronym Verification | Iterate and compare chars at each index. |
| 2325 | [Decode the Message](./problems/2325-decode-the-message.md) | Easy | Character Mapping | Secret Decoder Ring | Map key chars to alphabet, then substitute. |
| 459 | [Repeated Substring Pattern](./problems/459-repeated-substring-pattern.md) | Easy | String Matching | Wallpaper Pattern Matching | O(N) trick using string concatenation. |
| 1790 | [Check if One String Swap Can Make Strings Equal](./problems/1790-check-if-one-string-swap-can-make-strings-equal.md) | Easy | Index Tracking | Swapping books on a shelf. | Use an array to track differing indices. |
| 3106 | [Lexicographically Smallest String After Operations With Constraint](./problems/3106-lexicographically-smallest-string-after-operations-with-constraint.md) | Medium | Greedy | Adjusting a combination lock. | Iterate from left to right, making each character as small as possible. |

### Linked List Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|
| 21 | [Merge Two Sorted Lists](./problems/21-merge-two-sorted-lists.md) | Easy | Recursion, Iteration | Merging sorted data streams | Iterative approach is O(1) space |
| 83 | [Remove Duplicates from Sorted List](./problems/83-remove-duplicates-from-sorted-list.md) | Easy | Single Pointer, In-place | De-duplicating sorted train cars | O(N) time, O(1) space. A core pattern. |

### Stack & Queue Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|
| 1021 | [Remove Outermost Parentheses](./problems/1021-remove-outermost-parentheses.md) | Easy | Counter Simulation | Parentheses Parsing | A counter efficiently simulates a stack for depth tracking. |

### Tree Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---|---|---|---|---|
| 1530 | [Number of Good Leaf Nodes Pairs](./problems/1530-number-of-good-leaf-nodes-pairs.md) | Medium | DFS, Recursion | Finding "close" employees in an org chart. | Marked for review. Uses post-order DFS to find LCA. |
|---|---------|------------|--------------|-------------------|-------|
| 108 | [Convert Sorted Array to Binary Search Tree](./problems/108-convert-sorted-array-to-binary-search-tree.md) | Easy | Divide and Conquer, Recursion | Creating a fair tournament bracket. | 🚧 WIP. The key is picking the middle element as the root. |
| 100 | [Same Tree](./problems/100-same-tree.md) | Easy | Recursion, DFS, BFS | Comparing two company organization charts. | Classic recursive solution checking node values and structure. |
| 104 | [Maximum Depth of Binary Tree](./problems/104-maximum-depth-of-binary-tree.md) | Easy | DFS, Recursion | Finding the highest floor in a building. | Classic bottom-up recursion: `1 + max(left, right)`. |
| 543 | [Diameter of Binary Tree](./problems/543-diameter-of-binary-tree.md) | Easy | DFS, Recursion | Finding the longest path in a branching structure. | A dual-purpose recursive function is the key. |
| 94 | [Binary Tree Inorder Traversal](./problems/94-binary-tree-inorder-traversal.md) | Easy | Recursion, DFS | Librarian analogy for `Left -> Root -> Right`. | Standard recursive helper pattern is key. |
| 993 | [Cousins in Binary Tree](./problems/993-cousins-in-binary-tree.md) | Easy | BFS, Level-Order | Genealogist analogy for same depth, different parents. | BFS is natural for level-based problems. |
| 111 | [Minimum Depth of Binary Tree](./problems/111-minimum-depth-of-binary-tree.md) | Easy | BFS, DFS | Finding the shortest path to a fire escape. | BFS is optimal as it finds the first leaf level by level. |

### Graph Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|
| 785 | [Is Graph Bipartite?](./problems/785-is-graph-bipartite.md) | Medium | DFS, BFS, Union Find | Scheduling conflicting meetings. | Classic graph coloring problem. |

### Math Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|
| 3304 | [Find the K-th Character in String Game I](./problems/3304-find-the-k-th-character-in-string-game-i.md) | Easy | Recursion, Bit Manipulation | Building a fractal pattern | Optimal O(log k) solution using recursion. |
| 908 | [Smallest Range I](./problems/908-smallest-range-i.md) | Easy | Math | Adjusting building temperatures | The key is to only consider the min and max values. |
| 326 | [Power of Three](./problems/326-power-of-three.md) | Easy | Integer Limitation | Checking for perfect nesting in Russian dolls. | O(1) solution using the largest integer power of 3. |
| 3099 | [Harshad Number](./problems/3099-harshad-number.md) | Easy | Digit Sum, Divisibility | A number is a "Team Player" if it's divisible by its "teamwork contribution" (sum of digits). | Calculate digit sum, then check divisibility. |
| 3370 | [Smallest Number With All Set Bits](./problems/3370-smallest-number-with-all-set-bits.md) | Easy | Bitwise Generation | Finding a standard shipping box. | Generate `1, 3, 7, 15...` until `>= n`. |

### General Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|
| 3492 | [Maximum Containers on a Ship](./problems/3492-maximum-containers-on-a-ship.md) | Easy | Math, O(1) | Capacity planning | Direct calculation is better than search |
| 728 | [Self Dividing Numbers](./problems/728-self-dividing-numbers.md) | Easy | Math, Modulo | Number validation | Iterate and check digits with modulo |

### Bit Manipulation Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---|---|---|---|---|
| 3304 | [Find the K-th Character in String Game I](./problems/3304-find-the-k-th-character-in-string-game-i.md) | Easy | Recursion, Math | Building a fractal pattern | The string length doubles each time, a power-of-2 pattern. |
| 2859 | [Sum of Values at Indices With K Set Bits](./problems/2859-sum-of-values-at-indices-with-k-set-bits.md) | Easy | Bit Manipulation | Quality control inspector analogy. | Use bit manipulation to count set bits in an index `i`. |
|---|---------|------------|--------------|-------------------|-------|
| 3370 | [Smallest Number With All Set Bits](./problems/3370-smallest-number-with-all-set-bits.md) | Easy | Bitwise Generation | Finding a standard shipping box. | Generate `1, 3, 7, 15...` with `(x << 1) | 1`. |

### Design Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|
| 1603 | [Design Parking System](./problems/1603-design-parking-system.md) | Easy | O(1) State Management | Parking garage software | Countdown method simplifies state |
| 303 | [Range Sum Query - Immutable](./problems/303-range-sum-query-immutable.md) | Easy | Prefix Sum, O(1) Query | Road trip mileage log | Pre-computation for fast queries. |

### Dynamic Programming Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|

### Binary Search Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|
| 1337 | [The K Weakest Rows in a Matrix](./problems/1337-the-k-weakest-rows-in-a-matrix.md) | Easy | Sorting, Tie-breaking | Ranking teams in a tournament. | O(M log N + M log M) solution using binary search for counting and then sorting. |

### Two Pointers Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|
| 344 | [Reverse String](./problems/344-reverse-string.md) | Easy | In-place swap | Reversing books on a shelf | Optimal O(N) time, O(1) space solution. |
| 2563 | [Count the Number of Fair Pairs](./problems/2563-count-the-number-of-fair-pairs.md) | Medium | Sorting | Finding dance partners. | O(N log N) solution by sorting first. |
| 825 | [Friends Of Appropriate Ages](./problems/825-friends-of-appropriate-ages.md) | Medium | Sorting | Analyzing demographics at a large convention. | O(N) solution using age counting. |
| 2540 | [Minimum Common Value](./problems/2540-minimum-common-value.md) | Easy | Two Pointers, Array | Finding a common entry in two sorted lists. | Optimal O(N+M) time and O(1) space solution. |

### Sliding Window Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|
| 3258 | [Count Substrings That Satisfy K-Constraint I](./problems/3258-count-substrings-that-satisfy-k-constraint-i.md) | Easy | Nested Loops, Counting | Candy factory quality control. | O(N²) solution by checking all substrings with running counts. |
| 2269 | [Find the K-Beauty of a Number](./problems/2269-find-the-k-beauty-of-a-number.md) | Easy | Sliding Window, String | Stock data pattern analysis | O(L) time, single-pass solution. |

### Backtracking Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---------|------------|--------------|-------------------|-------|
| 561 | [Array Partition](./problems/561-array-partition.md) | Easy | Sorting | Maximizing dance competition scores. | Sort and sum every second element for the optimal result. |
| 1221 | [Split a String in Balanced Strings](./problems/1221-split-a-string-in-balanced-strings.md) | Easy | Counting | Balancing steps on a path | Split as soon as balance is 0 for max splits. |

### Greedy Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---|---|---|---|---|
| 3216 | [Lexicographically Smallest String After a Swap](./problems/3216-lexicographically-smallest-string-after-a-swap.md) | Easy | String | Optimizing a sequence with a single swap. | The first beneficial swap is always the best one. |
| 3684 | [Maximize Sum of At Most K Distinct Elements](./problems/3684-maximize-sum-of-at-most-k-distinct-elements.md) | Easy | Sorting, Hash Table | Packing a treasure chest. | Get unique elements with Set, sort descending, take top k. |
|---|---------|------------|--------------|-------------------|-------|
| 561 | [Array Partition](./problems/561-array-partition.md) | Easy | Greedy | Maximizing dance competition scores. | The key is to sort the array first. |
| 1337 | [The K Weakest Rows in a Matrix](./problems/1337-the-k-weakest-rows-in-a-matrix.md) | Easy | Binary Search, Tie-breaking | Ranking teams in a tournament. | O(M log N + M log M) solution using binary search for counting and then sorting. |

### Hash Table Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---|---|---|---|---|
| 3684 | [Maximize Sum of At Most K Distinct Elements](./problems/3684-maximize-sum-of-at-most-k-distinct-elements.md) | Easy | Greedy, Sorting | Packing a treasure chest. | Greedy: get unique elements with Set, sort descending, take top k. |
|---|---------|------------|--------------|-------------------|-------|
| 1995 | [Count Special Quadruplets](./problems/1995-count-special-quadruplets.md) | Easy | O(N³) Enumeration | Finding combinations that sum to a target. | Uses a frequency map to optimize a brute-force search from O(N⁴) to O(N³). |
| 3146 | [Permutation Difference between Two Strings](./problems/3146-permutation-difference-between-two-strings.md) | Easy | Two-Pass, Map | Calculating a "shuffling score" in a race. | Optimal O(N) time and O(K) space solution. |
| 387 | [First Unique Character in a String](./problems/387-first-unique-character-in-a-string.md) | Easy | Frequency Counter | Finding first unique element in a sequence | Two-pass scan for efficiency |
| 3663 | [Find The Least Frequent Digit](./problems/3663-find-the-least-frequent-digit.md) | Easy | Frequency Count, Two-Pass | Finding least-voted candidate | Optimal O(L) time, O(1) space solution. |
| 2744 | [Find Maximum Number of String Pairs](./problems/2744-find-maximum-number-of-string-pairs.md) | Easy | Simulation | Pairing socks from a pile of laundry. | Use a Set to track seen words and find pairs. |
| 2325 | [Decode the Message](./problems/2325-decode-the-message.md) | Easy | Substitution Cipher | Secret Decoder Ring | Build a map from key, then decode message. |
| 1790 | [Check if One String Swap Can Make Strings Equal](./problems/1790-check-if-one-string-swap-can-make-strings-equal.md) | Easy | Index Tracking | Swapping books on a shelf. | Use an array to track differing indices. |

### Sorting Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---|---|---|---|---|
| 3684 | [Maximize Sum of At Most K Distinct Elements](./problems/3684-maximize-sum-of-at-most-k-distinct-elements.md) | Easy | Greedy, Hash Table | Packing a treasure chest. | Get unique elements with Set, sort descending, take top k. |
|---|---------|------------|--------------|-------------------|-------|
| 2563 | [Count the Number of Fair Pairs](./problems/2563-count-the-number-of-fair-pairs.md) | Medium | Two Pointers | Finding dance partners. | O(N log N) solution using two pointers after sorting. |
|---|---------|------------|--------------|-------------------|-------|

### Matrix Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---|---|---|---|---|
| 1706 | [Where Will the Ball Fall](./problems/1706-where-will-the-ball-fall.md) | Medium | Direct Simulation | Pachinko machine simulation | Clean simulation is key. |

### Simulation Problems

| # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
|---|---|---|---|---|---|
| 1706 | [Where Will the Ball Fall](./problems/1706-where-will-the-ball-fall.md) | Medium | Direct Simulation | Pachinko machine simulation | Clean simulation is key. |