# 1603. Design Parking System

**Difficulty:** Easy
**Algorithm:** Design, Simulation
**Data Structure:** Array
**Date:** 2025-09-01

---

## 📝 Problem Description
Design a system to manage a parking lot with a fixed number of spots for three car sizes: big, medium, and small. The system must be able to quickly determine if a car of a certain size can be parked.

---

## 💡 Key Idea
The most efficient approach is to track the number of **remaining spots** for each car type. This is a "countdown" method. The `ParkingSystem` is initialized with the capacity for each car size. When a car arrives, the system checks if the count for its size is greater than zero. If it is, the count is decremented, and the car is admitted (`true`). Otherwise, it's turned away (`false`). This ensures every check and update is a simple, constant-time operation.

---

## 🧮 Complexity Analysis
- Time: O(1) for both the constructor and the `addCar` method. The operations are direct array/map lookups and decrements, which are not dependent on the number of cars or capacity.
- Space: O(1), as the system only requires a fixed-size data structure (e.g., an array of size 3) to store the counts, regardless of the number of `addCar` calls.

---

## 📖 Notes
- **Real-world analogy**: This system is a direct model of the software for a real parking garage gate. The `ParkingSystem` object is the gate's computer, initialized with spot counts. Each `addCar` call is a car arriving and the system making an instant O(1) decision to open the gate or display a "Lot Full" sign.
- **Design Choice**: Using an array to store the counts is highly effective, as the car types (1, 2, 3) can be directly mapped to indices. This is slightly more concise than using a hash map but achieves the same O(1) performance.
