1603. Design Parking System
Easy:Design/Simulation/Counting

### 生活/專案舉例 (Real-World Analogy)

Imagine you are building the software for the entry gate of a real parking garage.

The gate's computer is your `ParkingSystem` object.

  * When the garage opens, the manager tells the system how many spots of each size are available (`constructor(big, medium, small)`).
  * A car pulls up to the gate. A sensor determines its type (`carType`).
  * The car's driver pushes a button. This triggers your `addCar(carType)` method.
  * Your system needs to **instantly** (in O(1) time) decide if a spot is free.
      * If `true`, the gate opens, and your system internally notes that one spot is now taken.
      * If `false`, a "Lot Full" sign lights up.

The system must be fast, reliable, and accurately track the state of the garage. Your code is a perfect blueprint for this kind of real-world system.

-----

### 中文思路分析 (Chinese Thought Process)

#### 1\. 程式碼點評 (Code Review)

你的程式碼有很多值得稱讚的地方，它們都是軟體工程中的最佳實踐：

  * **`enum CarType`:** 使用列舉（Enum）而不是直接用數字 `1, 2, 3` 是個絕佳的選擇。它讓程式碼自我解釋（`CarType.Big` 比 `1` 更清晰），並且利用 TypeScript 的型別系統來防止傳入無效的車輛類型（例如 `4`）。
  * **封裝 (Encapsulation):** 使用私有欄位 (`#capacity`, `#status`) 是一個很好的封裝實踐。這意味著停車場的內部狀態只能透過你提供的 `addCar` 方法來修改，防止了外部程式碼意外地弄亂停車位的數量。
  * **清晰的狀態管理:** 將「總容量」(`capacity`) 和「目前使用量」(`status`) 分開追蹤，使得 `addCar` 中的邏輯 `this.#capacity[carType] > this.#status[carType]` 非常清晰易懂。

#### 2\. 提出修正策略 (A Minor Refinement)

你的解法已經很棒了。一個可以讓狀態管理更簡潔的微小改動是，我們其實不需要同時追蹤「總容量」和「目前數量」。我們只需要追蹤\*\*「剩餘車位」\*\*即可。這種「倒數計時」的思路在很多資源管理的場景中都很常見。

**倒數計時法 (Countdown Method):**

1.  在 `constructor` 中，直接用一個陣列或物件儲存每個類型**剩餘**的車位數量。
2.  在 `addCar` 中，檢查對應類型的剩餘車位是否大於 0。
3.  如果大於 0，就將該數量減 1，並返回 `true`。
4.  否則，直接返回 `false`。

這個方法將兩個狀態變數 (`#capacity`, `#status`) 簡化為了一個。

-----

#### 3\. 複雜度分析與優化建議

  * **你的解法 & 倒數計時法:**

      * **時間複雜度: O(1)** for both `constructor` and `addCar`. 無論有多少車位或呼叫多少次 `addCar`，每次操作（物件屬性存取、比較、遞增/遞減）都是固定時間的。這對於像停車閘門這樣需要即時反應的系統至關重要。
      * **空間複雜度: O(1)**。你的類別只使用了固定數量的變數來儲存三種類型的車位資訊。儲存空間不會隨著呼叫次數的增加而增長。

  * **優化建議:**

      * **你的解法已經是最佳解了！** 在時間和空間複雜度上，你都達到了 O(1)，這是最快的。
      * 這裡的「優化」並非針對效能，而是針對**設計模式**。上面提到的「倒數計時法」在程式碼上稍微簡潔一點（少了一個狀態變數），是另一種同樣優秀的實現方式。在面試中，能夠討論這兩種狀態管理方式的細微差別（追蹤 `(status, capacity)` vs 追蹤 `spotsRemaining`）會是一個亮點。

-----

### English Explanation & Final Code

#### Code Review & Best Practices

Your solution demonstrates several software engineering best practices:

  * **Enums for Type Safety:** Using an `enum` for `CarType` makes the code self-documenting and prevents bugs from "magic numbers" (like `1`, `2`, `3`).
  * **Encapsulation:** Using private fields (`#`) correctly hides the internal state of your class, ensuring it can only be modified via the `addCar` method.
  * **Clear State Management:** Separating `capacity` and `status` makes the logic in `addCar` explicit and easy to understand.

#### The "Countdown" Refinement

Your solution is great. A minor alternative that simplifies the state management is to only track the **spots remaining**, rather than both capacity and usage.

**Countdown Method:**

1.  In the `constructor`, store the initial counts of available spots.
2.  In `addCar`, check if the count for that `carType` is greater than 0.
3.  If it is, decrement that count and return `true`.
4.  Otherwise, return `false`.

This reduces the state from two records/objects to just one.

-----

#### Complexity Analysis & Optimization Suggestions

  * **Time Complexity: O(1)** for both `constructor` and `addCar`. Each operation is a simple, constant-time lookup and comparison. This is crucial for a system that needs to respond instantly.

  * **Space Complexity: O(1)**. The class uses a fixed amount of space to store the counts for the three car types, regardless of how many `addCar` calls are made.

  * **Optimization Suggestions:**

      * **Your solution is already optimal** in terms of time and space complexity.
      * The only "optimization" is a discussion of design patterns. The "countdown" method is a slightly more concise way to manage the state. Being able to discuss the trade-offs between tracking `(status, capacity)` vs. `spotsRemaining` is a sign of a thoughtful developer.

### Final TypeScript Code (Countdown Method)

This version implements the slightly more concise "countdown" state management. An array is used here for simplicity, as `carType` 1, 2, 3 can map to indices 0, 1, 2.

```typescript
class ParkingSystem {
    // We use an array to store the remaining spots.
    // Index 0: big, Index 1: medium, Index 2: small
    private spots: number[];

    constructor(big: number, medium: number, small: number) {
        // The carType (1, 2, 3) will be 1-indexed, so we can place a dummy
        // value at index 0 to make the mapping direct: this.spots[carType].
        this.spots = [0, big, medium, small];
    }

    addCar(carType: 1 | 2 | 3): boolean {
        // Check if there are any remaining spots for the given carType.
        if (this.spots[carType] > 0) {
            // If yes, decrement the count of available spots.
            this.spots[carType]--;
            // Grant access to the car.
            return true;
        }
        
        // If no spots are available, deny access.
        return false;
    }
}

/**
 * Your ParkingSystem object will be instantiated and called as such:
 * var obj = new ParkingSystem(big, medium, small)
 * var param_1 = obj.addCar(carType)
 */
```