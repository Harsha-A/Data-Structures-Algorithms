Below is a **one-page DFS / BFS explanation cheat sheet** you can **memorize**, **revise before interviews**, and **recite confidently**.

This is optimized for **FAANG / Google Noogler interviews**.

---

# 🧠 DFS / BFS CHEAT SHEET (INTERVIEW-READY)

---

## 🔹 1. What is DFS?

**DFS (Depth-First Search)** explores **one path completely** before backtracking.

### 🎤 1-Line Interview Explanation

> “DFS explores as far as possible along one branch before backtracking, and is useful for exploring or marking connected components.”

---

### 🧩 When to Use DFS

* Count islands / regions
* Check reachability
* Traverse entire structure
* Detect cycles (with state)

---

### 🧱 DFS Grid Template (JS)

```js
function dfs(r, c) {
  if (
    r < 0 || r >= ROWS ||
    c < 0 || c >= COLS ||
    visited[r][c]
  ) return;

  visited[r][c] = true;

  for (const [dr, dc] of directions) {
    dfs(r + dr, c + dc);
  }
}
```

---

### ⏱️ Complexity

* **Time:** `O(V + E)` → `O(R × C)` for grid
* **Space:** `O(R × C)` (visited + recursion stack)

---

### 🚫 DFS Pitfalls

❌ Forgetting visited
❌ Stack overflow on large grids
❌ Using DFS for shortest path

---

## 🔹 2. What is BFS?

**BFS (Breadth-First Search)** explores **level by level** using a queue.

### 🎤 1-Line Interview Explanation

> “BFS explores nodes level by level and guarantees the shortest path in unweighted graphs.”

---

### 🧩 When to Use BFS

* Shortest path
* Minimum steps
* Minimum time
* Spread / infection problems
* Distance from nearest source

---

### 🧱 BFS Grid Template (JS)

```js
const queue = [[startR, startC]];
visited[startR][startC] = true;

while (queue.length) {
  const [r, c] = queue.shift();

  for (const [dr, dc] of directions) {
    const nr = r + dr, nc = c + dc;

    if (
      nr >= 0 && nr < ROWS &&
      nc >= 0 && nc < COLS &&
      !visited[nr][nc]
    ) {
      visited[nr][nc] = true;
      queue.push([nr, nc]);
    }
  }
}
```

---

### ⏱️ Complexity

* **Time:** `O(V + E)`
* **Space:** `O(V)`

---

### 🚫 BFS Pitfalls

❌ Forgetting to mark visited early
❌ Using BFS when DFS is simpler
❌ Using BFS without a queue

---

## 🔹 3. DFS vs BFS — Decision Table

| Problem asks…     | Use |
| ----------------- | --- |
| Count groups      | DFS |
| Reachability      | DFS |
| Shortest path     | BFS |
| Minimum time      | BFS |
| Flood / spread    | BFS |
| Tree traversal    | DFS |
| Large grid safety | BFS |

---

## 🔹 4. Multi-Source BFS / DFS

### When?

* Multiple starting points
* Gates, oceans, rotten oranges

---

### 🎤 Explanation

> “Instead of one source, I push all sources into the queue initially and run BFS normally.”

---

### 🧱 Multi-Source BFS Template

```js
for (const [r, c] of sources) {
  queue.push([r, c]);
  visited[r][c] = true;
}
```

---

## 🔹 5. Grid = Graph Mental Model

![Image](https://blogs.cornell.edu/info2040/files/2017/09/2-y6ixtc.png)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240216084522/bfs-vs-dfs-%281%29.png)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240215173832/BFS_1tree.png)

* Cell = node
* Up/Down/Left/Right = edges
* Visited = prevent cycles

---

## 🔹 6. Ultra-Short Emergency Explanation (20s)

> “DFS explores depth-wise and is good for marking connected components.
> BFS explores level-wise using a queue and guarantees shortest paths or minimum time.”

---

## 🔹 7. Interview Keywords (SAY THESE)

* Visited set
* Queue / recursion stack
* Connected component
* Level by level
* Shortest path
* Multi-source BFS

---

## 🔹 8. Common Interview Trap Questions

### ❓ Why BFS gives shortest path?

> “Because BFS explores nodes in increasing distance order in an unweighted graph.”

---

### ❓ Why visited is needed?

> “To avoid revisiting nodes and infinite loops.”

---

## 🔹 9. Pattern Memory Trick

> **DFS → Structure**
> **BFS → Distance**

If you remember this, you’ll choose correctly 90% of the time.

---

## 🔹 10. Final Interview Tip

**Explain first. Code later.**
If your explanation is clear, interviewers already trust your code.

---
