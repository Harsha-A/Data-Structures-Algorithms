Perfect — let’s do a **true grid basics crash course**, step by step, exactly in the **2–3 day structure** you mentioned.
I’ll assume **no prior comfort with grids** and build you up to Pacific–Atlantic naturally.

---

# 🧠 GRID BASICS CRASH COURSE (INTERVIEW-READY)

---

# 🟢 DAY 1 — 2D ARRAYS + NEIGHBORS

*(Foundation — don’t skip this)*

---

## 1️⃣ What is a 2D array?

A **2D array** is just an array of arrays.

```js
const grid = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];
```

Think of it like a **table**:

![Image](https://courses.cs.washington.edu/courses/cse121/test/resources/cheatsheets/images/2D_Array_Visual.png)

![Image](https://www.mathworks.com/company/technical-articles/matrix-indexing-in-matlab/_jcr_content/mainParsys/columns_1735561276/c3733e7f-5a71-4d62-ac3f-bbd01c7a2563/image.adapt.full.medium.jpg/1727193217514.jpg)

![Image](https://mathsfirst.massey.ac.nz/Algebra/CoordSystems/images/gr1.gif)

| Row ↓ / Col → | 0 | 1 | 2 |
| ------------- | - | - | - |
| **0**         | 1 | 2 | 3 |
| **1**         | 4 | 5 | 6 |
| **2**         | 7 | 8 | 9 |

---

## 2️⃣ What does `grid[r][c]` mean?

* `r` → row index
* `c` → column index

```js
grid[0][0] // 1 (top-left)
grid[1][2] // 6
grid[2][1] // 8
```

📌 **Rule to memorize**

> First index = vertical movement
> Second index = horizontal movement

---

## 3️⃣ Looping over a grid (VERY IMPORTANT)

```js
const ROWS = grid.length;
const COLS = grid[0].length;

for (let r = 0; r < ROWS; r++) {
  for (let c = 0; c < COLS; c++) {
    console.log(r, c, grid[r][c]);
  }
}
```

Interviewers expect this to be **muscle memory**.

---

## 4️⃣ Neighbors (up, down, left, right)

Every cell has **at most 4 neighbors**.

![Image](https://i.sstatic.net/5L9nV.jpg)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240424142803/Adjacency-Matrix-for-Directed-and-Unweighted-graph.webp)

### Direction vectors (MEMORIZE)

```js
const directions = [
  [1, 0],   // down
  [-1, 0],  // up
  [0, 1],   // right
  [0, -1]   // left
];
```

---

## 5️⃣ Boundary check (CRITICAL)

```js
if (
  nr >= 0 &&
  nr < ROWS &&
  nc >= 0 &&
  nc < COLS
)
```

📌 **Most bugs happen here**

---

## ✅ Day 1 takeaway

You must be able to say instantly:

* What `grid[r][c]` means
* How to get neighbors
* How to avoid going outside the grid

---

# 🟡 DAY 2 — DFS ON A GRID + VISITED MATRIX

---

## 1️⃣ What is DFS in a grid?

DFS = **go deep**, explore connected cells.

Grid = implicit graph:

* Each cell = node
* Neighbors = edges

---

## 2️⃣ Why do we need a visited matrix?

Without it:

* Infinite loops
* Re-visiting same cell again and again

```js
const visited = Array.from(
  { length: ROWS },
  () => Array(COLS).fill(false)
);
```

---

## 3️⃣ Basic DFS template (MEMORIZE)

```js
function dfs(r, c) {
  // base cases
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

## 4️⃣ Example: Count islands

```js
if (grid[r][c] === 1 && !visited[r][c]) {
  dfs(r, c);
  islands++;
}
```

📌 **Each DFS marks one connected component**

---

## 5️⃣ Interview mental model

> DFS = “Mark everything connected to me”

This is why it’s used for:

* Islands
* Regions
* Components

---

## ✅ Day 2 takeaway

You should know:

* When to use DFS
* Why visited is needed
* That DFS explores *connected regions*

---

# 🔵 DAY 3 — MULTI-SOURCE BFS / DFS

This is the **bridge** to Pacific–Atlantic.

---

## 1️⃣ What is “multi-source”?

Instead of **one starting point**, you start from **many**.

Examples:

* All gates
* All rotten oranges
* All ocean-border cells

---

## 2️⃣ Multi-source BFS (distance / time)

```js
const queue = [];

for (each source) {
  queue.push(source);
  visited[source] = true;
}

while (queue.length) {
  const [r, c] = queue.shift();
  for (neighbors) {
    if (!visited[nr][nc]) {
      visited[nr][nc] = true;
      queue.push([nr, nc]);
    }
  }
}
```

Each BFS level = **time / distance**

---

## 3️⃣ Multi-source DFS (reachability)

Pacific–Atlantic uses **this**.

```js
for (each ocean-border cell) {
  dfs(r, c);
}
```

📌 All DFS calls share the **same visited matrix**

---

## 4️⃣ Why this matters

Instead of:
❌ DFS from every cell (slow)

We do:
✅ DFS from borders once (fast)

This is the **reverse reachability pattern**.

---

## 5️⃣ Mental bridge to Pacific–Atlantic

| Concept  | Pacific–Atlantic |
| -------- | ---------------- |
| Grid     | heights          |
| Sources  | ocean borders    |
| DFS rule | move uphill      |
| Result   | intersection     |

---

## 🧠 FINAL CONNECTION (VERY IMPORTANT)

Pacific–Atlantic is NOT a “new” problem.

It is simply:

* Day 1: grid indexing
* Day 2: DFS + visited
* Day 3: multi-source DFS
* * one trick: **reverse direction**

---

## 🎯 If you master these 3 days

You can solve:

* Pacific Atlantic
* Number of islands
* Rotting oranges
* Surrounded regions
* Walls & gates

---

## ✅ What you should practice next (order)

1️⃣ Number of Islands
2️⃣ Flood Fill
3️⃣ Walls and Gates
4️⃣ Rotting Oranges
5️⃣ Pacific Atlantic Water Flow

---
