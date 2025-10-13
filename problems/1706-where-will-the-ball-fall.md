# 1706. Where Will the Ball Fall

**Difficulty:** Medium  
**Algorithm:** Simulation  
**Data Structure:** Array, Matrix  
**Date:** 2025-10-13  

---

## 📝 Problem Description
This problem simulates a Plinko or Pachinko machine. We are given a 2D grid representing pegs. A `1` directs a ball to the right, and a `-1` directs it to the left. We need to determine the final column for a ball dropped from the top of each starting column. A ball gets stuck if it hits a wall or a "V" shaped pocket formed by adjacent, opposing pegs.

---

## Real-world analogy
Imagine a **Plinko or Pachinko machine** at a carnival. You drop a ball from the top, and it bounces off a series of pegs (`1`s and `-1`s in our grid) on its way down. The goal is to predict which slot the ball will land in at the bottom.

A ball can get stuck in two ways:
1.  **Hitting a Wall:** A peg near the edge directs the ball off the side of the machine.
2.  **Hitting a "V" Shape:** Two adjacent pegs point towards each other (e.g., a `1` next to a `-1`), creating a V-shaped pocket that traps the ball, preventing it from falling further.

Our task is to simulate this process for a ball dropped in every possible starting slot and report where it ends up, or if it gets stuck.

---

## 💡 Key Idea
The most straightforward and robust approach is a **direct simulation**. We can iterate through each starting column, dropping one virtual ball at a time. For each ball, we then simulate its journey row by row. In each row, we check the direction of the peg (`1` or `-1`) and determine the next column. Before moving the ball, we must validate the move by checking for the two "stuck" conditions: hitting a wall (going out of bounds) or entering a "V" trap (the peg in the destination column points in the opposite direction). If either condition is met, the ball is stuck (`-1`); otherwise, we update its column and proceed to the next row.

---

## 🧮 Complexity Analysis
- Time: `O(M * N)`, where M is the number of rows and N is the number of columns. We simulate N balls, and each simulation takes at most M steps.
- Space: `O(N)` to store the output array. If we exclude the space for the answer, the auxiliary space is O(1).

---

## 📖 Notes
- Real-world analogy: Simulating a Plinko or Pachinko machine.
- Edge cases considered: ball starting at the leftmost or rightmost column, "V" shaped traps.
- The key is to check for invalid moves (wall collisions or V-traps) *before* updating the ball's position for the next row.
