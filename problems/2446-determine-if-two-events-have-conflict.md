# 2446. Determine if Two Events Have Conflict

**Difficulty:** Easy
**Algorithm:** Direct String Comparison
**Data Structure:** Array, String
**Date:** 2025-09-27

---

## 📝 Problem Description

Given two events represented by their start and end times `[startTime, endTime]`, determine if there is a conflict between them. A conflict occurs if the time intervals overlap. The time is given in `HH:MM` format.

---

## Real-world analogy

This is exactly like checking your calendar for overlapping meetings.

You have Meeting A (`event1`) and Meeting B (`event2`). A conflict exists if one meeting starts before the other one has finished. For example, if Meeting A is from 10:00 to 11:00 and Meeting B is from 10:30 to 11:30, they overlap. The easiest way to check for an overlap is to see if Meeting A starts before Meeting B ends, AND Meeting B starts before Meeting A ends.

---

## 💡 Key Idea

The core insight is that because the time format is fixed as `"HH:MM"`, time strings can be compared directly (lexicographically). For instance, `"10:30"` is less than `"11:00"`. This avoids the need to parse hours and minutes.

A conflict exists if and only if `event1`'s start time is less than or equal to `event2`'s end time, AND `event2`'s start time is less than or equal to `event1`'s end time. This can be expressed in a single line: `start1 <= end2 && start2 <= end1`.

---

## 🧮 Complexity Analysis

- **Time:** `O(1)` because a fixed number of string comparisons are performed.
- **Space:** `O(1)` because a constant amount of extra space is used.

---

## 📖 Notes

- Real-world analogy: Checking for overlapping appointments in a calendar system.
- The key simplification is to compare time strings directly instead of parsing them, which is less error-prone and more concise.
