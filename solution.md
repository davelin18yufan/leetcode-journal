993. Cousins in Binary Tree

Binary tree
BFS(breadth first search)

### 生活/專案舉例 (Real-World Analogy)

Imagine you're a genealogist looking at a large family tree. You're asked, "Are Alice and Bob cousins?"

To answer this, you need to find out two things for both Alice and Bob:

1.  **Their Generation (Depth):** Are they in the same generation? (e.g., are they both great-grandchildren of the family's founder?)
2.  **Their Parents:** Do they have different parents?

If they are in the **same generation** but have **different parents**, they are cousins. If they're in different generations, or if they have the same parents (making them siblings), they are not cousins.

Your `findNode` function was trying to find their generation (`depth`), but it was missing the crucial step of also identifying their parent.

### 中文除錯與思路分析 (Chinese Debugging & Thought Process)

#### 1\. 分析與肯定你的思路

你已經意識到需要搜尋節點並檢查它們的深度，這是解題的第一步。但你的 `findNode` 函式在幾個地方遇到了困難：

  * **遺失資訊:** 函式沒有辦法記錄或返回節點的**父節點**是誰。
  * **遞迴邏輯:** 遞迴呼叫 `findNode(node.left, ...)` 的結果沒有被使用，資訊無法從深層傳遞回來。
  * **狀態管理:** `depth` 變數在遞迴呼叫中被錯誤地傳遞和修改 (`depth++`)。

#### 2\. 思路探索 (A Better Traversal Strategy)

這個問題有兩個條件：「深度相同」和「父節點不同」。對於任何涉及「層級」或「深度」的樹問題，**廣度優先搜尋 (BFS / Level-Order Traversal)** 都是一個非常自然且高效的選擇。

BFS 的工作方式就像在水中投下一塊石頭，漣漪會一層一層地向外擴散。我們可以用這個方法來逐層掃描我們的樹。

#### 3\. 提出修正策略 (The BFS Approach)

**演算法:**

1.  我們需要一個**佇列 (Queue)** 來實現 BFS。佇列是一種「先進先出」(First-In, First-Out) 的資料結構。
2.  在 BFS 的每一層，我們都檢查是否同時找到了 `x` 和 `y`。
3.  我們還需要在遍歷時記錄每個節點的父節點。一個簡單的方法是在佇列中不僅儲存節點本身，還儲存它的父節點。
4.  **改進：** 一個更聰明的 BFS 方法是，我們在處理**父節點**那一層時，就直接檢查它的**子節點**是不是 `x` 和 `y`。這樣可以更容易地判斷它們是否有相同的父節點。

**BFS 精簡演算法:**

1.  建立一個佇列，並將根節點 `root` 推入。
2.  開始 `while` 迴圈，只要佇列不為空就繼續。
3.  在每一層開始時，記錄下當前層的節點數量 `levelSize`。我們將處理這麼多次。
4.  在處理當前層的迴圈中，用兩個布林變數 `foundX = false` 和 `foundY = false` 來記錄是否在**這一層**找到了 `x` 和 `y`。
5.  在 `levelSize` 迴圈中：
      * 從佇列中取出一個節點 `currentNode`。
      * 檢查它的**子節點**：
          * `if (currentNode.left && currentNode.right)`，如果 `currentNode` 的左右子節點剛好是 `x` 和 `y`（順序不限），那麼它們的父節點相同，直接返回 `false`。
          * 如果 `currentNode` 的任一子節點的值是 `x` 或 `y`，就更新對應的 `foundX` 或 `foundY` 旗標。
          * 將非空的子節點加入佇列，供下一層處理。
6.  在處理完一整層（`levelSize` 迴圈結束後）後：
      * 如果 `foundX` 和 `foundY` **都**是 `true`，表示它們在同一層（深度相同）且我們已經排除了它們父節點相同的情況。返回 `true`。
      * 如果只有一個是 `true`，表示它們在不同層。返回 `false`。
7.  如果整個 BFS 結束了，就返回 `false`（儘管根據題目約束，這種情況不會發生）。

### 複雜度分析與優化建議

  * **BFS 解法:**

      * **時間複雜度: O(N)**，其中 N 是樹中的節點數量。在 BFS 中，我們需要訪問每一個節點恰好一次。
      * **空間複雜度: O(W)**，其中 W 是樹的最大寬度。這是佇列在某一時刻可能儲存的最大節點數量。在最壞的情況下（一個完美的、茂盛的二元樹），W 可能接近 N/2，所以空間複雜度也可以寫作 O(N)。

  * **優化建議:**

      * 對於需要比較「深度」或進行「逐層」操作的樹問題，**廣度優先搜尋 (BFS) 通常是最直觀且高效的演算法**。
      * 它避免了遞迴（深度優先搜尋 DFS）可能帶來的呼叫堆疊深度問題，並且讓我們可以在找到答案後（例如，發現 `x` 和 `y` 在不同層）立即停止，而不需要遍歷整棵樹的其餘部分。這個 BFS 解法已經是此問題的最佳解。

### English Explanation & Final Code

#### Debugging & Thought Process

Your main challenge was correctly tracking both the **depth** and the **parent** of the target nodes. A recursive function can do this, but it gets complicated. For any tree problem that involves levels or depths, a **Breadth-First Search (BFS)** is often a much cleaner and more direct approach.

BFS explores the tree level by level, which perfectly matches the "same depth" requirement of the problem.

#### The Optimal Strategy: Breadth-First Search (BFS)

**Algorithm:**

1.  Use a **Queue** to store nodes for the level-order traversal.
2.  Iterate through the tree one level at a time.
3.  For each level, check if we find `x` and `y` among the children of the nodes from the *previous* level.
4.  During the traversal of a level's nodes:
      * Keep track if `x` was found on this level (`foundX`) and if `y` was found (`foundY`).
      * Crucially, check if any single node is the parent of **both** `x` and `y`. If so, they are siblings, not cousins, so we can immediately return `false`.
5.  After a full level is processed:
      * If `foundX` and `foundY` are both true, they have the same depth and we've confirmed they have different parents. Return `true`.
      * If only one of them is true, they are at different depths. Return `false`.

#### Complexity Analysis & Optimization Suggestions

  * **BFS Solution:**

      * **Time Complexity: O(N)**, where N is the number of nodes. Each node is enqueued and dequeued exactly once.
      * **Space Complexity: O(W)**, where W is the maximum width of the tree. This is for the space in the queue. In the worst case (a complete binary tree), this can be O(N).

  * **Optimization Suggestions:**

      * This BFS approach is **optimal** for this problem. It naturally handles the level-based requirements and can terminate early if it finds `x` and `y` are on different levels.

### Final TypeScript Code (BFS)

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

function isCousins(root: TreeNode | null, x: number, y: number): boolean {
    if (!root) {
        return false;
    }

    // A queue for our BFS traversal.
    const queue: TreeNode[] = [root];

    while (queue.length > 0) {
        const levelSize = queue.length;
        let foundX = false;
        let foundY = false;

        // Process all nodes at the current level.
        for (let i = 0; i < levelSize; i++) {
            const node = queue.shift()!; // Dequeue the next node

            // --- Check if this node is the parent of both x and y ---
            if (node.left && node.right) {
                if (
                    (node.left.val === x && node.right.val === y) ||
                    (node.left.val === y && node.right.val === x)
                ) {
                    return false; // They are siblings, not cousins.
                }
            }

            // --- Check if we've found x or y at this level ---
            if (node.left && (node.left.val === x || node.left.val === y)) {
                if (node.left.val === x) foundX = true;
                if (node.left.val === y) foundY = true;
            }
            if (node.right && (node.right.val === x || node.right.val === y)) {
                if (node.right.val === x) foundX = true;
                if (node.right.val === y) foundY = true;
            }
            
            // --- Enqueue children for the next level ---
            if (node.left) {
                queue.push(node.left);
            }
            if (node.right) {
                queue.push(node.right);
            }
        }
        
        // --- After processing the level, check our findings ---
        if (foundX && foundY) {
            return true; // Found both at the same depth with different parents.
        }
        if (foundX || foundY) {
            return false; // Found one but not the other, so they are at different depths.
        }
    }

    return false;
}
```