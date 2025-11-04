# 3160. Find the Number of Distinct Colors Among the Balls

**Difficulty:** Medium  
**Algorithm:** Simulation, Hash Table  
**Data Structure:** Array, Hash Table  
**Date:** 2025-11-04  

---

## 📝 Problem Description

You are given a series of queries. Each query assigns a color to a specific ball. Your task is to process these queries and, after each one, report the total number of *distinct* colors that are currently assigned to any ball.

---

## 👕 Real-world analogy (T-Shirt Inventory)

This problem is like managing T-shirt colors for a sports team.

- `queries`: A list of requests, e.g., "Give player 10 a red shirt."
- `map (ball -> color)`: This is your **player roster**. It tells you which color T-shirt each player *currently* has. `[Player 10 -> Blue]`.
- `colors (color -> count)`: This is your **inventory count of shirts *in use***. `[Blue -> 5], [Red -> 3]`.

When a request `[Player 10, Red]` comes in:

1.  **Check Roster:** You look at your roster (`map`) and see Player 10 *used to have* a `Blue` shirt.
2.  **Decrement Old Color:** You go to your `Blue` inventory box (`colors`) and decrease its count from 5 to 4. If the box becomes empty, you remove it from your active inventory.
3.  **Increment New Color:** You go to your `Red` inventory box and increase its count from 3 to 4.
4.  **Update Roster:** You update your player roster to `[Player 10 -> Red]`.
5.  **Report:** The number of distinct colors is the number of inventory boxes with at least one shirt in them (`colors.size`).

---

## 💡 Key Idea

The core of the solution is to maintain two states: the current color of each ball and the frequency of each color being used.

1.  A hash map, `ballToColor`, tracks the current color of each ball (`ball -> color`). This is essential to know the *previous* color when a ball is reassigned.
2.  A second hash map, `colorFrequency`, tracks how many balls are currently of a certain color (`color -> count`).

For each query:
- If the ball had a previous color, decrement the count for that old color in `colorFrequency`. If the count drops to zero, remove that color entry entirely.
- Increment the count for the new color in `colorFrequency`.
- Update the ball's color in `ballToColor`.
- The number of distinct colors is simply the `size` of the `colorFrequency` map.

---

## 🧮 Complexity Analysis

- Time: `O(N)` where `N` is the number of queries. Each query involves a constant number of hash map operations, which are `O(1)` on average.
- Space: `O(Q)` where `Q` is the number of unique balls and colors. In the worst case, this is proportional to `N`, the number of queries.

---

## 📖 Notes
- Real-world analogy: Managing a dynamic inventory system where items are assigned different categories.
- Edge cases considered: A ball being assigned the same color it already has, a new ball being introduced, a color count dropping to zero.
