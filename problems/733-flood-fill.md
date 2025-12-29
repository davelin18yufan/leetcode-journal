# 733. Flood Fill

**Difficulty:** Easy  
**Algorithm:** Depth-First Search, Breadth-First Search  
**Data Structure:** Array, Matrix  
**Date:** 2025-12-29  

---

## 📝 Problem Description
The Flood Fill algorithm is used to fill a connected region of a multi-dimensional array with a new value. Starting from a given seed point, it changes the value of all points in the connected component of the seed point that have the same original value. This is analogous to the "paint bucket" tool in image-editing software.

---

## Real-world analogy
Imagine using the "Paint Bucket" tool in an application like Photoshop. When you click on a blue area of an image with the color red selected, the tool finds all adjacent blue pixels connected to where you clicked and repaints them red. It stops when it hits a pixel of a different color, which acts as a boundary. This is a perfect real-world example of Flood Fill. It's used for region filling in image editors, identifying connected areas in map analysis, or even determining reachable spaces for a robot's pathfinding algorithm.

---

## 💡 Key Idea
The core idea is to use a graph traversal algorithm, either Depth-First Search (DFS) or Breadth-First Search (BFS), to visit all connected pixels of the same starting color.

1.  **Store Start Color**: Record the color of the starting pixel `(sr, sc)`.
2.  **Handle Edge Case**: If the starting color is already the target color, there's nothing to do. Return the image immediately to prevent an infinite loop.
3.  **Traversal**:
    *   **DFS (Recursive)**: Create a helper function that takes coordinates `(r, c)`.
        - **Base Cases**: Stop if the coordinates are out of bounds or if the pixel at `(r, c)` is not of the `startColor`.
        - **Action**: Change the color of the current pixel to the new `color`.
        - **Recurse**: Call the function for the four neighbors (up, down, left, right).
    *   **BFS (Iterative)**: Use a queue and start with the seed point. While the queue is not empty, dequeue a pixel, color it, and enqueue its valid, unvisited neighbors of the same starting color.

---

## 🧮 Complexity Analysis
- **Time Complexity**: `O(M*N)`, where `M` and `N` are the number of rows and columns in the image. In the worst case, we visit every pixel once.
- **Space Complexity**: `O(M*N)` in the worst case for the recursion stack (DFS) or the queue (BFS). This happens when the entire image is of the same color.

---

## 📖 Notes
- **Real-world analogy**: "Paint Bucket" tool in graphics software.
- **Key Edge Case**: If the starting color is the same as the new color, returning early is crucial to avoid an infinite recursion stack overflow.
- **8-Directional Fill**: The problem can be extended to include diagonals by simply adding four more recursive/iterative calls for the diagonal neighbors.
- **BFS as an alternative**: Using BFS with a queue can avoid deep recursion stacks, which might be a concern for very large, contiguous areas.
