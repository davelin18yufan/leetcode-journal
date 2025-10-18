# 1732. Find the Highest Altitude

**Difficulty:** Easy  
**Algorithm:** Prefix Sum  
**Data Structure:** Array  
**Date:** 2025-10-18  

---

## 📝 Problem Description
You are given an integer array `gain` of length `n` where `gain[i]` is the net gain in altitude between points `i` and `i + 1` for all (`0 <= i < n)`. Return the **highest altitude** of a point. The biker starts at altitude `0`.

---

## Real-world analogy
This problem is exactly like **tracking your bank account balance** during a day of shopping.

  * You start with $0 (`altitude = 0`).
  * The `gain` array is your list of transactions (e.g., `[-5, +1, +5]`).
  * Your `sum` variable is your **current balance**.
  * Your `max` variable is the **highest balance** you had at any point during the day.

You start with a max of $0 (your starting balance). After the first transaction (`-5`), your balance is -$5, but your max is still $0. After the next (`+1`), your balance is -$4, max is still $0. After the next (`+5`), your balance is $1. Now, $1 is greater than $0, so your new max is $1. Your code does exactly this.

---

## 💡 Key Idea
The core idea is to simulate the process of the biker's journey. We can maintain a running sum representing the current altitude. We start at an altitude of 0, and also initialize our maximum altitude seen so far to 0. Then, we iterate through the `gain` array, updating the current altitude at each step. After each update, we compare the current altitude with the maximum altitude seen so far and update the maximum if the current altitude is higher.

---

## 🧮 Complexity Analysis
- Time: `O(N)`, where N is the length of the `gain` array, because we iterate through the array once.
- Space: `O(1)`, as we only use a few variables to store the current and maximum altitudes.

---

## 📖 Notes
- Real-world analogy: Tracking bank account balance.  
- The initial altitude is 0, which is also a potential candidate for the highest altitude.
- Edge cases considered: empty `gain` array, all negative gains, all positive gains.
