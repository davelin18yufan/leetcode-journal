# 1797. Design Authentication Manager

**Difficulty:** Medium
**Algorithm:** Hash Table, Design
**Data Structure:** Hash Table
**Date:** 2025-12-08

---

## 📝 Problem Description
Design a system that manages authentication tokens. It should allow generating new tokens with a fixed time-to-live, renewing existing tokens, and counting the number of unexpired tokens at any given moment.

---

## Real-world analogy
Imagine you're a security guard at a large, exclusive event with a strict time-based entry policy. Each guest is given a temporary pass (a token) with a specific expiration time printed on it.

-   **`generate(tokenId, currentTime)`**: When a new guest arrives, you issue them a new pass (`tokenId`). You look at the current time (`currentTime`), add the event's duration (`timeToLive`), and write down the exact expiration time on the pass. You keep a logbook (`#validTokenIds`) where you record the guest's ID and their pass's expiration time.

-   **`renew(tokenId, currentTime)`**: A guest inside the event wants to extend their stay. They come to you with their pass. First, you check your logbook. If their pass is still valid (i.e., it hasn't expired yet), you update its expiration time in your logbook to `currentTime + timeToLive`. If their pass has already expired when they ask, you do nothing—they've missed their chance.

-   **`countUnexpiredTokens(currentTime)`**: The event manager asks you for a headcount of currently active guests. You don't just count the people inside; you must go through your entire logbook. For each entry, you compare its expiration time to the current time (`currentTime`). Any pass that is expired is crossed out from your logbook. Finally, you count the remaining valid entries and give that number to the manager. The key is that this "cleaning" of the logbook happens every time you're asked for a count, or when you generate or renew a pass, ensuring your records are always up-to-date.

This system ensures that only valid, unexpired tokens (passes) are considered active, with a mechanism to periodically purge old ones.

---

## 💡 Key Idea
The core of the solution is a hash map that stores `tokenId` as the key and its `expirationTime` as the value. A critical design choice is to *not* passively wait for tokens to expire. Instead, expiration is actively checked and cleared during each operation (`generate`, `renew`, `countUnexpiredTokens`). This "lazy deletion" or "just-in-time cleaning" approach ensures that any query to the system operates on a consistently up-to-date set of tokens. By centralizing the cleanup logic in a private helper method (`#removeExpired`), we avoid code duplication and ensure all public methods are synchronized with the current time.

---

## 🧮 Complexity Analysis
- Time: `O(N)` for `generate`, `renew`, and `countUnexpiredTokens`, where `N` is the number of active tokens at the time of the call. This is because each call may trigger a full scan of all tokens to remove expired ones.
- Space: `O(N)` to store the active tokens in the hash map.

---

## 📖 Notes
- The provided solution is an optimized approach where expired tokens are removed just-in-time during each operation.
- This avoids the need for a separate background process or more complex data structures like a min-heap, providing a simple and effective solution for the given constraints.
