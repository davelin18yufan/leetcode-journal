# 3492. Maximum Containers on a Ship

**Difficulty:** Easy  
**Algorithm:** Math  
**Data Structure:** N/A  
**Date:** 2025-08-31  

---

## 📝 Problem Description
The goal is to determine the maximum number of containers a ship can hold. This is constrained by two factors: the physical space on the ship's deck, which can fit `n * n` containers, and the ship's maximum weight capacity, `maxWeight`, where each container has a uniform weight `w`.

---

## 💡 Key Idea
The solution avoids a slow iterative search by reframing the problem as a direct calculation. The number of containers is limited by both space (`n * n`) and weight (`maxWeight / w`). Since both constraints must be satisfied, the actual maximum number of containers is simply the **minimum** of these two values. This provides a constant-time O(1) solution.

---

## 🧮 Complexity Analysis
- **Time:** O(1) - The solution involves a few simple arithmetic calculations that do not depend on the input size.
- **Space:** O(1) - Only a few variables are used to store the calculated limits, resulting in constant space usage.

---

## 📖 Notes
- **Real-world analogy:** Imagine you're buying candy. You have a budget (`maxWeight`) and each candy has a price (`w`). You can calculate how many you can afford (`maxWeight / w`). You also have a physical limit to how many you can carry (`n*n`). You can only take the number of candies that satisfies both your budget and your carrying capacity, which will be the minimum of the two.
- **Edge cases considered:** The solution handles cases where the weight limit is very low (e.g., `maxWeight` is less than `w`, resulting in 0 containers) and where the space limit is the constraining factor.
