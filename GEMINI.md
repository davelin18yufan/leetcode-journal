This repository is designed to systematically record my **LeetCode practice**.  
All modification **must strictly follow the rules below**.
All files has to be written in English.

---

## 📋 1. README.md Structure

The `README.md` file is the **master index** of all solved problems.  

It contains two sections

**Statistics**
- **Total Problems Solved**
- **Count by difficulty**: 0
- **Last Updated Date**

**Quick Search Index**
- All problems listed here possess reference link to detail file.

---

## 2. All problems classified into **three marlfown files**:

1. **Complete Problems Table**
`by_status.md`

   ```md
   ## 📋 Complete Problems Table

   | # | Problem | Difficulty | Algorithm | Data Structure | Real-world Scenario | Status | Date |
   |---|---------|------------|-----------|----------------|-------------------|---------|------|
  ```

* **Append new rows only** (never modify old ones unless fixing errors).
* **Date** = today’s date in `YYYY-MM-DD`.

---

2. **Problems by Category**
`by_category.md`

   ```md
   ## 📚 Problems by Category

   ### <Category Name> Problems

   | # | Problem | Difficulty | Key Concepts | Real-world Scenario | Notes |
   |---|---------|------------|--------------|-------------------|-------|
   ```

   * Each problem must be inserted into the correct **category section** (Stack, Array, String, Tree, Graph, General).
   * If the category does not exist, create a new section with the above format.
   * Notes must briefly describe approach (1 sentence, not full solution).

---

3. **Problems by Difficulty**
`by_difficulty.md`

   ```md
   ## 🎯 Problems by Difficulty

   ### Easy Problems
   - [1. Two Sum](#array-problems)
   - [20. Valid Parentheses](#stack-problems)
   ```

   * Each problem must appear under its **difficulty** (Easy / Medium / Hard).
   * Use internal anchor link to category section (e.g., `#stack-problems`).
   * Keep the list **chronological by problem number**.



---

## 📂 3. Problem-Specific Files

Each solved problem **must also have a markdown file** inside `/problems/`:

File format:

```
problems/<num>-<kebab-case-title>.md
```

Example:

```
problems/20-valid-parentheses.md
```

### File Template:

```md
# 20. Valid Parentheses

**Difficulty:** Easy  
**Algorithm:** Stack Simulation  
**Data Structure:** Stack  
**Date:** 2025-08-24  

---

## 📝 Problem Description
(Short summary of problem in your own words.)

---

## Real-world analogy
(Illustration about how the problems might occured in real world scenarios.)

---

## 💡 Key Idea
(Brief explanation of the main algorithmic insight, e.g. "Use a stack to track open brackets and ensure each closing bracket matches the latest open one.")

---

## 🧮 Complexity Analysis
- Time: `O(N)` 
- Space: `O(N)`

---

## 📖 Notes
- Real-world analogy: Checking balanced brackets in a code editor.  
- Edge cases considered: empty string, mismatched closing bracket, extra opening bracket.
```

---

## ⚠️ 3. Constraints for LLM Contributions

1. **Do not change existing entries** (only append new problems).
2. **Follow exact markdown table alignment** (use `|` consistently).
3. **Anchor links must match category headings** (case-insensitive).
4. **Dates must always be today’s date (YYYY-MM-DD).**
5. **Each problem must exist in all three places:**

   * `Complete Problems Table`
   * `Category Table`
   * `Difficulty List`
   * (plus a dedicated `/problems/*.md` file)
6. **Calculate total count and update mermaid chart at the top after every update.**
7. **Real world analogy description around 50 ~ 200 words.** (easy to imaginated.)
8. **If target problem which is already on list, check status on list and update.**
9. **Data inserted into the category file must in ascending order by question number.**
10. **If found problem done before**
   * if solved, add second time status with different color based on situation.
   * if not solved, add second time status with different color based on situation and marked there still required next times.

---

✅ If any of the above rules are not followed, the contribution must be **rejected**.

