108. Convert Sorted Array to Binary Search Tree
easy
Array
Divide and Conquer
Tree
Binary Search Tree
Binary Tree

### \#\# Real-World Analogy

This problem is exactly like creating a **fair tournament bracket** for a competition where players are ranked (seeded) from best to worst. The `nums` array is your list of ranked players.

To make the bracket as balanced as possible, you don't have the \#1 and \#2 seeds play each other right away. Instead, you:

1.  **Pick the player in the exact middle** of the ranking. They are the "final boss" and will be the **root** of your tournament tree.
2.  All the players in the **first half** of the list (those with better rankings) are put into the **left side of the bracket**.
3.  All the players in the **second half** of the list are put into the **right side of the bracket**.
4.  How do you build the left and right brackets? You apply the **exact same logic recursively**\! You find the middle player of that smaller group to be the "semi-final boss," and so on, until you're left with individual matchups.

### \#\# Chinese Thought Process

#### \#\#\#\# Code Review & Debugging

你的遞迴想法 `sortedArrayToBST(nums.slice(left, start))` 是完全正確的。讓我們把它變成完整的程式碼。

  * **遞迴的作用:** `sortedArrayToBST` 這個函式的作用應該是：接收一個排序好的陣列，並**返回**由這個陣列構成的平衡二元搜尋樹的**根節點**。
  * **你的 `while` 迴圈問題:** 迭代法（使用 `while` 迴圈）來建立樹結構通常非常複雜，因為你需要手動管理節點和它們的子節點關係。遞迴法則讓這個過程變得非常自然。

#### \#\#\#\# The Recursive Strategy

我們來嚴格執行「建立比賽支架」的邏輯。

**Algorithm (基於你的 `slice` 想法):**

1.  **Base Case (終止條件):** 如果傳入的 `nums` 陣列是空的，表示這個分支沒有選手了，返回 `null`。
2.  **Find the Middle (選出 Boss):** 找到陣列的中間索引 `mid`。
3.  **Create the Root (建立節點):** 用中間的元素 `nums[mid]` 建立當前的根節點 `root`。
4.  **Build Subtrees (遞迴建立左右賽區):**
      * `root` 的左子樹，就是由 `mid` 左邊的所有元素構成的。所以我們呼叫 `root.left = sortedArrayToBST(nums.slice(0, mid));`
      * `root` 的右子樹，就是由 `mid` 右邊的所有元素構成的。所以我們呼叫 `root.right = sortedArrayToBST(nums.slice(mid + 1));`
5.  **Return the Root:** 返回我們剛剛建立的 `root` 節點。

#### \#\#\#\# Complexity Analysis & Optimization

  * **`slice` 解法的複雜度:**
      * **時間複雜度: O(N log N)**。在遞迴的每一層，`slice()` 操作都需要複製一部分陣列，這是一個 O(N) 的操作。樹的高度是 O(log N)，所以總體是 O(N log N)。
      * **空間複雜度: O(N log N)**。因為每次遞迴都會建立新的陣列副本。
  * **優化建議 (使用索引代替 `slice`):**
      * 為了避免 `slice()` 帶來的高昂複製成本，標準的最佳解法是寫一個輔助函式，它在**同一個**原始陣列上操作，但使用**左右索引（指針）** 來標示當前需要處理的範圍。
      * 這樣可以將**時間複雜度優化到 O(N)**（因為每個元素只被訪問一次），並將**空間複雜度降至 O(log N)**（遞迴堆疊的高度）。

-----

### \#\# English Explanation & Final Code

#### \#\#\#\# From `while` loop to your better `slice` idea

Your iterative `while` loop attempt is difficult to implement. Your second idea, `sortedArrayToBST(nums.slice(...))`, is much better and is the foundation for the classic recursive solution.

The function `sortedArrayToBST(nums)` should do one job: take a sorted array and **return the root node** of a balanced BST built from that array.

**Algorithm (based on your `slice` idea):**

1.  **Base Case:** If the `nums` array is empty, return `null`.
2.  **Find the Middle:** Find the middle index `mid`.
3.  **Create the Root:** Create a new `TreeNode` using the middle element `nums[mid]`.
4.  **Build Subtrees (The Recursive Step):**
      * The root's `left` child is the result of calling the same function on the left half of the array: `root.left = sortedArrayToBST(nums.slice(0, mid));`
      * The root's `right` child is the result of calling it on the right half: `root.right = sortedArrayToBST(nums.slice(mid + 1));`
5.  **Return:** Return the `root` you just created.

#### \#\#\#\# Complexity Analysis & Optimization

  * **`slice` Version:**
      * **Time Complexity: O(N log N)** because `.slice()` is an O(N) operation that is performed at each level of the recursion (log N levels).
      * **Space Complexity: O(N log N)** due to the storage of the sliced array copies.
  * **Optimization Suggestion (Using Pointers/Indices):**
      * The standard optimal solution avoids the costly `.slice()` operation. It uses a recursive helper function that is passed `left` and `right` indices to define the part of the original array it should work on. This improves the **time complexity to O(N)** and **space complexity to O(log N)** (for the recursion stack). This is the version you'd want to use in an interview.

### \#\# Final Code (Optimal Pointer-Based Recursion)

This code implements the optimized pointer-based strategy.

```typescript
class TreeNode {
    val: number
    left: TreeNode | null
    right: TreeNode | null
    constructor(val?: number, left?: TreeNode | null, right?: TreeNode | null) {
        this.val = (val === undefined ? 0 : val)
        this.left = (left === undefined ? null : left)
        this.right = (right === undefined ? null : right)
    }
}

function sortedArrayToBST(nums: number[]): TreeNode | null {
    // A helper function that works with indices instead of slicing the array.
    function buildTree(left: number, right: number): TreeNode | null {
        // Base Case: If the left pointer crosses the right, this segment is empty.
        if (left > right) {
            return null;
        }

        // 1. Find the middle of the current segment.
        const mid = Math.floor((left + right) / 2);
        
        // 2. Create the root node with the middle element.
        const root = new TreeNode(nums[mid]);

        // 3. Recursively build the left and right subtrees.
        // The left subtree is built from the left half of the current segment.
        root.left = buildTree(left, mid - 1);
        // The right subtree is built from the right half.
        root.right = buildTree(mid + 1, right);
        
        // 4. Return the constructed root node.
        return root;
    }

    // Start the recursive process on the entire array (from index 0 to length - 1).
    return buildTree(0, nums.length - 1);
}

// Example 1 Test
console.log(sortedArrayToBST([-10,-3,0,5,9])); 
// Expected: A balanced tree rooted at 0.
```