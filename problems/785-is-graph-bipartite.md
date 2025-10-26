# 785. Is Graph Bipartite?

**Difficulty:** Medium  
**Algorithm:** Depth-First Search, Breadth-First Search, Union Find  
**Data Structure:** Graph  
**Date:** 2025-10-26  

---

## 📝 Problem Description
A graph is bipartite if its vertices can be divided into two independent sets, U and V, such that every edge in the graph connects a vertex in U to one in V. This is equivalent to checking if the graph can be colored with two colors, such that no two adjacent vertices have the same color.

---

## Real-world analogy
Imagine you are organizing a large conference and you need to schedule a series of meetings. Some pairs of attendees cannot be in the same meeting room at the same time because they need to be in different places. You can represent the attendees as nodes and the scheduling conflicts as edges. The graph is "bipartite" if you can divide all attendees into two groups (e.g., "Morning Session Group" and "Afternoon Session Group") such that no two people with a conflict are in the same group. If you can do this, you can run all the necessary meetings in just two time slots. If not, the graph is not bipartite, and you'll need more than two time slots.

---

## 💡 Key Idea
The core idea is to "color" the graph with two colors. We can traverse the graph using Breadth-First Search (BFS) or Depth-First Search (DFS). We assign the first color to a starting node. Then, for each of its neighbors, we assign the second color. For each of their uncolored neighbors, we assign the first color, and so on. If we ever find a neighbor that is already colored with the same color as the current node, we have a conflict, and the graph is not bipartite.

---

## 🧮 Complexity Analysis
- Time: `O(N + E)`, where N is the number of nodes and E is the number of edges.
- Space: `O(N)` for the color array and the queue/recursion stack.

---

## 📖 Notes
- This problem is a classic application of graph traversal (BFS or DFS).
- The graph might be disconnected, so we need to iterate through all nodes to handle all components.
- Marked as "Pending" for future review as requested.
