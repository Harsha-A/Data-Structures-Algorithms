Below is a **clean, from-scratch, Noogler-level explanation of Graphs** — exactly what interviewers **expect you to already know** before asking DFS/BFS problems.

No heavy theory. No university jargon. Just **interview-useful fundamentals**.

---

# 🧠 Graph Basics — Noogler DE Interview Level

[Pre Read for Graphs](#Pre-Read-for-Graphs)

---

## 1️⃣ What is a Graph? (Say this confidently)

> **A graph is a collection of nodes connected by edges, used to model relationships.**

That’s it.

Examples interviewers love:

* Cities ↔ Roads
* Courses ↔ Prerequisites
* Users ↔ Friendships
* Grid cells ↔ Neighbors

---

## 2️⃣ Core Terminology (MUST KNOW)

| Term          | Meaning                              |
| ------------- | ------------------------------------ |
| Node (Vertex) | An entity                            |
| Edge          | Connection between nodes             |
| Neighbor      | Directly connected node              |
| Degree        | Number of edges of a node            |
| Path          | Sequence of connected nodes          |
| Cycle         | Path that starts & ends at same node |
| Connected     | Path exists between nodes            |

🎤 Interview sentence:

> “Each node represents ___ and edges represent ___.”

---

## 3️⃣ Types of Graphs (Very Important)

### 🔹 Undirected Graph

Edges work **both ways**.

```
A — B
```

Example:

* Friend relationships
* Network cables

---

### 🔹 Directed Graph

Edges work **one way**.

```
A → B
```

Example:

* Course prerequisites
* Task dependencies

---

### 🔹 Weighted vs Unweighted

| Type       | Meaning         |
| ---------- | --------------- |
| Unweighted | All edges equal |
| Weighted   | Edges have cost |

📌 **Most Noogler problems are unweighted**.

---

## 4️⃣ Graph Representation (INTERVIEW GOLD)

### ✅ Adjacency List (DEFAULT CHOICE)

```js
const graph = {
  0: [1, 2],
  1: [3],
  2: [],
  3: []
};
```

Meaning:

* Node `0` connects to `1` and `2`
* Node `1` connects to `3`

🎤 Interview sentence:

> “I’ll use an adjacency list for efficient traversal.”

---

### ❌ Adjacency Matrix (Rare)

```js
[
  [0,1,1],
  [0,0,1],
  [0,0,0]
]
```

Used only if graph is **tiny or very dense**.

---

## 5️⃣ Grid as a Graph (CRITICAL – 50% QUESTIONS)

Most people miss this.

![Image](https://blogs.cornell.edu/info2040/files/2017/09/2-y6ixtc.png)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240424142803/Adjacency-Matrix-for-Directed-and-Unweighted-graph.webp)

### How a grid becomes a graph:

| Grid               | Graph       |
| ------------------ | ----------- |
| Cell `(r,c)`       | Node        |
| Up/Down/Left/Right | Edges       |
| Boundary           | Graph limit |
| Visited matrix     | Visited set |

This is why **grid problems = graph problems**.

---

## 6️⃣ Traversal: DFS vs BFS (ENGINE OF GRAPHS)

### 🔹 DFS (Depth-First Search)

* Go deep first
* Uses recursion or stack
* Best for **exploring structure**

Used for:

* Connected components
* Islands
* Reachability

🎤 Interview sentence:

> “DFS explores one path fully before backtracking.”

---

### 🔹 BFS (Breadth-First Search)

* Go level by level
* Uses queue
* Best for **shortest path / time**

Used for:

* Minimum steps
* Shortest path
* Spread problems

🎤 Interview sentence:

> “BFS explores level by level and guarantees shortest path in unweighted graphs.”

---

## 7️⃣ Visited Set (NON-NEGOTIABLE)

Without visited:

* Infinite loops
* Repeated work

```js
visited[node] = true;
```

🎤 Interview sentence:

> “I maintain a visited set to avoid revisiting nodes.”

---

## 8️⃣ Connected Components (VERY COMMON)

### What is it?

A group of nodes where **every node is reachable from every other node**.

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20220905132251/graph.jpg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A900/1%2ACZZ4vemV157olFPDywqY1g.png)

### Key rule:

> **One DFS/BFS = one component**

Used in:

* Number of Islands
* Friend Circles
* Provinces

🎤 Interview sentence:

> “Each DFS marks one connected component.”

---

## 9️⃣ Cycles (Why interviewers care)

Cycles mean:

* Infinite loops
* Invalid dependency order

### Undirected graph

* DFS + parent check

### Directed graph

* DFS with **3 states**:

  * `0` = unvisited
  * `1` = visiting
  * `2` = visited

🎤 Interview sentence:

> “If I encounter a visiting node again, a cycle exists.”

---

## 🔟 Topological Sort (Dependencies)

### When you see:

* “Prerequisite”
* “Dependency”
* “Order of tasks”

You should think:

> **Topological sort**

Meaning:

> An order where dependencies come first

Used in:

* Course Schedule
* Build systems

---

## 🧠 How Interviewers Expect You to Think

They don’t want:
❌ Fancy math
❌ Graph theory proofs

They want:
✅ Can you **model the problem** as a graph?
✅ Can you **choose DFS or BFS correctly**?
✅ Can you **explain your choice**?

---

## 🎯 One-Line Graph Detection Rule (MEMORIZE)

> **If I can describe the problem as nodes and relationships, it’s a graph.**

---

## ✅ What You Should Be Able To Do After This

* Identify graph problems in 10–15 seconds
* Say **DFS or BFS** and why
* Explain graph modeling before coding
* Avoid brute force naturally

---

## 🚀 What to Learn Next (Recommended Order)

1. DFS & BFS templates
2. Connected components
3. Cycle detection
4. Topological sort
5. Multi-source BFS

---

Perfect — below are **DETAILED, INTERVIEW-READY NOTES on the *prerequisites*** for the **Course Schedule (Can Finish Courses)** problem.

This is written the way **Google expects a Noogler / SDE-3 candidate to *understand before coding***.

---

# 📘 Detailed Prerequisite Notes

### Course Schedule (Cycle Detection in Directed Graph)

---

## 0️⃣ What This Question Is REALLY Testing

> This question is **NOT** about coding DFS.
> It tests whether you understand:

* **Dependencies**
* **Directed graphs**
* **Why cycles break feasibility**
* **How DFS recursion state works**

If you miss any prerequisite below, the solution becomes memorization.

---

## 1️⃣ Directed Graph Fundamentals (ABSOLUTE MUST)

### 🔹 What is a Directed Graph?

A graph where edges have direction.

```
A → B
```

Means:

> You must finish **B before A**

### 🔹 How This Maps to the Problem

* **Node** → Course
* **Directed Edge** → Prerequisite

```js
[course, prerequisite]
```

So:

```txt
[0, 1]  ⇒  0 → 1
```

Meaning:

> To take course 0, you must first take course 1

---

### 🔹 Why This Is Not an Undirected Graph

Dependencies are **one-way**.

```
Course 1 does NOT depend on Course 0
```

This matters because:

* **Cycle detection logic is different**
* Parent tracking (used in undirected graphs) does NOT work here

---

## 2️⃣ Graph Representation (Adjacency List)

### 🔹 Why Adjacency List?

Because:

* `numCourses` up to 1000
* Sparse dependencies
* Efficient traversal

```js
Map<Course, [Prerequisites]>
```

Example:

```txt
0 → [1, 2]
1 → [3]
2 → []
3 → []
```

This means:

* Course 0 depends on 1 and 2
* Course 1 depends on 3

---

### 🔹 Why Not Adjacency Matrix?

* Matrix = O(N²)
* Wasteful for sparse graphs
* Slower iteration

🧠 **Interview expectation**:

> “I used adjacency list for O(V + E) traversal.”

---

## 3️⃣ Cycle in Directed Graph (CORE CONCEPT)

### 🔹 What Is a Cycle?

A path that starts and ends at the same node **following directions**.

```
0 → 1 → 2 → 0
```

![Image](https://media.geeksforgeeks.org/wp-content/uploads/cycle-BFS.png)

![Image](https://blog.mrinalini.dev/img/graphs_dfs_directed_course_select.jpg)

### 🔹 Why Cycle = Impossible?

Because:

* Each course waits on another
* No course can be started

📌 **This is the key logic leap Google wants**

> “If a dependency cycle exists, no valid ordering exists.”

---

## 4️⃣ DFS Traversal (FOUNDATIONAL SKILL)

You must know DFS **beyond syntax**.

### 🔹 DFS Meaning

> “Explore as deep as possible before backtracking.”

### 🔹 DFS Call Stack Reality

Each recursive call:

* Pauses the caller
* Adds a frame to the call stack

This stack = **current dependency chain**

---

## 5️⃣ Recursion Stack Tracking (MOST IMPORTANT PREREQUISITE)

### 🔹 Why `visiting` Exists

```js
const visiting = new Set();
```

This tracks:

> **Nodes in the current DFS path**

NOT:

* All visited nodes
* All processed nodes

---

### 🔹 Three Logical States (VERY IMPORTANT)

Even if code uses Sets, you must understand this model:

| State | Meaning             | Code Representation             |
| ----- | ------------------- | ------------------------------- |
| White | Never visited       | Not in map/set                  |
| Gray  | Currently exploring | `visiting.has(node)`            |
| Black | Fully processed     | `preMap.get(node).length === 0` |

---

### 🔹 Cycle Detection Rule (MEMORIZE)

> If DFS reaches a **Gray** node → **cycle**

This is why:

```js
if (visiting.has(crs)) return false;
```

---

## 6️⃣ Backtracking (DFS Hygiene)

### 🔹 What Is Backtracking?

Undoing state after recursion completes.

```js
visiting.add(crs);
// explore children
visiting.delete(crs);
```

Why needed?

* Prevent false cycle detection
* Clean recursion path

🧠 Interview test:

> “What breaks if you forget to remove from `visiting`?”

---

## 7️⃣ Memoization / Pruning in DFS

This line is **not optional understanding**:

```js
preMap.set(crs, []);
```

### 🔹 What It Means Conceptually

> “This node is confirmed safe.
> No need to re-check its dependencies.”

### 🔹 Why This Is Correct

Because:

* All its prerequisites were already verified
* DFS guarantees correctness before reaching here

### 🔹 Without This

* Algorithm still correct
* But may become O(N²)

---

## 8️⃣ Disconnected Graphs

Courses may form **multiple independent graphs**.

```
0 → 1

2 → 3
```

So you must:

```js
for (let c = 0; c < numCourses; c++) {
    dfs(c);
}
```

🧠 Interview check:

> “Why not start from course 0 only?”

---

## 9️⃣ Relation to Topological Sort (CONCEPTUAL PREREQ)

You must know:

### 🔹 Definition

Topological sort = ordering where:

```
prerequisite comes before dependent
```

### 🔹 Key Fact

> A directed graph has a topological order **iff** it has **no cycle**

This problem is asking:

> “Does a valid topological ordering exist?”

DFS cycle detection answers that.

---

## 🔟 Complexity Analysis (NON-NEGOTIABLE)

You must be fluent with:

### Time

```
O(V + E)
```

Why?

* Each node processed once
* Each edge explored once

### Space

```
O(V + E)  (graph)
O(V)      (recursion + visiting set)
```

---

## 🧠 Mental Model Summary (MEMORIZE THIS)

> “This problem models course dependencies as a directed graph.
> A cycle makes completion impossible.
> DFS with recursion stack tracking detects cycles efficiently.”

If you say this naturally → **Noogler ready**.

---

==========================================================


Awesome 👍
Here’s **both** things you asked for:

1️⃣ **1-page printable cheat sheet**
2️⃣ **Step-by-step DFS execution trace (whiteboard style)**

Keep this bookmarked — this alone is enough to **never get confused in Course Schedule again**.

---

# 🧾 1-PAGE CHEAT SHEET

### Course Schedule / Directed Cycle Detection

---

## 🧠 Problem Recognition

If the problem mentions:

* prerequisites
* dependencies
* must be done before
* ordering feasibility

👉 **It’s a directed graph + cycle detection problem**

---

## 🧩 Graph Modeling

* **Node** → Course
* **Edge** → `course → prerequisite`
* **Cycle** → Impossible to finish

---

## 🎯 Core Idea (MEMORIZE)

> A directed graph can be completed **iff** it has **no cycle**

---

## 🔁 DFS State Model (CRITICAL)

| State | Meaning                        |
| ----- | ------------------------------ |
| WHITE | Not visited                    |
| GRAY  | Visiting (in current DFS path) |
| BLACK | Fully processed (safe)         |

Cycle rule:

> **If DFS reaches a GRAY node → cycle**

---

## 🧠 DFS Logic (Whiteboard Pseudocode)

```
dfs(node):
    if node is GRAY → cycle → return false
    if node is BLACK → already safe → return true

    mark node GRAY
    for each prerequisite:
        if dfs(prerequisite) is false:
            return false

    mark node BLACK
    return true
```

---

## 🧹 Why Memoization Works

```js
preMap.set(course, []);
```

Meaning:

> “This course and all its dependencies are verified safe — skip next time”

✔ Improves performance
✔ Does NOT affect correctness

---

## 🔗 Disconnected Graphs

Always do:

```
for each course:
    dfs(course)
```

Because dependencies may be in multiple components.

---

## ⏱ Complexity

* **Time:** `O(V + E)`
* **Space:** `O(V + E)` (graph + recursion stack)

---

## 🎯 Interview Power Line (USE THIS)

> “This is directed cycle detection using DFS with recursion stack tracking.”

---

---

# 🧑‍🏫 STEP-BY-STEP DFS TRACE (WHITEBOARD GOLD)

Let’s trace this input:

```js
numCourses = 3
prerequisites = [[0,1],[1,2],[2,0]]
```

Graph:

```
0 → 1 → 2 → 0
```

![Image](https://media.geeksforgeeks.org/wp-content/uploads/cycle-BFS.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AvUNiYpY1_0lsZZwHuVvIEw.gif)

---

## 🔍 Step 1 — Start DFS from Course 0

```
visiting = {}
```

Call:

```
dfs(0)
```

Mark:

```
visiting = {0}
```

---

## 🔍 Step 2 — Explore Prerequisite of 0 → 1

```
dfs(1)
```

Mark:

```
visiting = {0, 1}
```

---

## 🔍 Step 3 — Explore Prerequisite of 1 → 2

```
dfs(2)
```

Mark:

```
visiting = {0, 1, 2}
```

---

## 🚨 Step 4 — Explore Prerequisite of 2 → 0

```
dfs(0)
```

Check:

```
visiting.has(0) === true
```

🔥 **CYCLE DETECTED**

Return `false` all the way up.

---

## ❌ Final Result

```
return false
```

👉 **Courses cannot be completed**

---

## 🧠 What the Interviewer Wants to Hear Here

> “We revisited a node that was already in the current DFS path, which proves a circular dependency.”

That sentence = ✅ **strong signal**

---

# 🔁 Now Compare with a VALID Case

```js
prerequisites = [[0,1],[1,2]]
```

Graph:

```
0 → 1 → 2
```

Trace:

* 2 finishes → BLACK
* 1 finishes → BLACK
* 0 finishes → BLACK

✔ No node revisited while GRAY
✔ Valid schedule exists

---

# 🧠 FINAL 20-SECOND SUMMARY (MEMORIZE)

> “I model courses as a directed graph. Using DFS with recursion stack tracking, if I revisit a node currently in the stack, I’ve found a cycle and return false. Otherwise, if all nodes finish safely, the courses can be completed.”

---

================================================================

## Pre Read for Graphs

Perfect set of topics 👍 — this **exact bundle** covers ~70% of graph interview questions (including Google / Amazon / Meta).

Below is a **complete JS-first study guide** with:

* Clear **mental models**
* **Reusable templates**
* **When to use what**
* **Classic LeetCode examples**
* **Interview tips**

---

# 🧠 Graphs – Core Study Guide (JS)

## How to think about Graph Problems

Before code, always answer these **3 questions**:

1. **Is the graph directed or undirected?**
2. **Do I need to visit all nodes or stop early?**
3. **Am I detecting a structure?**

   * Connectivity → DFS/BFS
   * Cycle → DFS state / indegree
   * Ordering → Topological sort
   * Distance / spread → BFS (often multi-source)

---

## 1️⃣ DFS & BFS Templates (FOUNDATION)

![Image](https://he-s3.s3.amazonaws.com/media/uploads/9fa1119.jpg)

![Image](https://he-s3.s3.amazonaws.com/media/uploads/fdec3c2.jpg)

### DFS – Recursive (Most Used)

**Use when**: explore fully, detect cycles, components

```js
function dfs(node, adj, visited) {
  if (visited.has(node)) return;
  visited.add(node);

  for (const nei of adj[node]) {
    dfs(nei, adj, visited);
  }
}
```

### DFS – Iterative (Stack)

```js
function dfsIterative(start, adj) {
  const stack = [start];
  const visited = new Set();

  while (stack.length) {
    const node = stack.pop();
    if (visited.has(node)) continue;

    visited.add(node);
    for (const nei of adj[node]) {
      stack.push(nei);
    }
  }
}
```

---

### BFS – Queue (Shortest path, levels)

**Use when**: shortest distance, layers, spread

```js
function bfs(start, adj) {
  const queue = [start];
  const visited = new Set([start]);

  while (queue.length) {
    const node = queue.shift();
    for (const nei of adj[node]) {
      if (!visited.has(nei)) {
        visited.add(nei);
        queue.push(nei);
      }
    }
  }
}
```

🔑 **DFS vs BFS**

| DFS              | BFS            |
| ---------------- | -------------- |
| Deep exploration | Level by level |
| Recursion-heavy  | Queue-based    |
| Cycle detection  | Shortest path  |

---

## 2️⃣ Connected Components

![Image](https://dist.neo4j.com/wp-content/uploads/20190215062515/graph-algorithms-strongly-connected-components-3.jpg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2ARf98vgvcLle1SZvLmmIwaQ.png)

### Problem Pattern

> “How many groups / islands / networks exist?”

### Undirected Graph

```js
function countComponents(n, edges) {
  const adj = Array.from({ length: n }, () => []);
  for (const [u, v] of edges) {
    adj[u].push(v);
    adj[v].push(u);
  }

  const visited = new Set();
  let components = 0;

  for (let i = 0; i < n; i++) {
    if (!visited.has(i)) {
      dfs(i, adj, visited);
      components++;
    }
  }
  return components;
}
```

### Classic Problems

* Number of Islands
* Connected Components in Undirected Graph
* Friend Circles

🧠 **Interview insight**
Each DFS/BFS call = **1 component**

---

## 3️⃣ Cycle Detection

![Image](https://cdn.prod.website-files.com/6828da5fc9f6eba971cc609f/6875fe520803aae135b55d9f_Detect%20Cycle%20in%20Directed%20Graph%20using%20BFS.jpg)

![Image](https://cdn.prod.website-files.com/6828da5fc9f6eba971cc609f/68794708b7add34a5f920cdb_Detect%20cycle%20in%20an%20undirected%20graph%20.jpg)

### A) Directed Graph (MOST IMPORTANT)

👉 Use **3 states**

| State | Meaning                       |
| ----- | ----------------------------- |
| 0     | Unvisited                     |
| 1     | Visiting (in recursion stack) |
| 2     | Visited                       |

```js
function hasCycleDirected(n, edges) {
  const adj = Array.from({ length: n }, () => []);
  for (const [u, v] of edges) adj[u].push(v);

  const state = Array(n).fill(0);

  function dfs(node) {
    if (state[node] === 1) return true;  // cycle
    if (state[node] === 2) return false;

    state[node] = 1;
    for (const nei of adj[node]) {
      if (dfs(nei)) return true;
    }
    state[node] = 2;
    return false;
  }

  for (let i = 0; i < n; i++) {
    if (dfs(i)) return true;
  }
  return false;
}
```

📌 **Used in**

* Course Schedule
* Dependency resolution

---

### B) Undirected Graph

👉 Track **parent**

```js
function hasCycleUndirected(n, edges) {
  const adj = Array.from({ length: n }, () => []);
  for (const [u, v] of edges) {
    adj[u].push(v);
    adj[v].push(u);
  }

  const visited = new Set();

  function dfs(node, parent) {
    visited.add(node);
    for (const nei of adj[node]) {
      if (!visited.has(nei)) {
        if (dfs(nei, node)) return true;
      } else if (nei !== parent) {
        return true;
      }
    }
    return false;
  }

  for (let i = 0; i < n; i++) {
    if (!visited.has(i) && dfs(i, -1)) return true;
  }
  return false;
}
```

---

## 4️⃣ Topological Sort (ORDERING PROBLEMS)

![Image](https://i.imgur.com/Q3MA6dZ.png)

![Image](https://i.sstatic.net/0154o.png)

### When do you use this?

* Tasks with **dependencies**
* “Order of execution”
* Course Schedule II

---

### A) DFS-based Topological Sort

```js
function topoSortDFS(n, edges) {
  const adj = Array.from({ length: n }, () => []);
  for (const [u, v] of edges) adj[u].push(v);

  const visited = new Set();
  const result = [];

  function dfs(node) {
    if (visited.has(node)) return;
    visited.add(node);

    for (const nei of adj[node]) dfs(nei);
    result.push(node);
  }

  for (let i = 0; i < n; i++) dfs(i);
  return result.reverse();
}
```

---

### B) Kahn’s Algorithm (BFS + Indegree) ⭐⭐⭐

**Preferred in interviews**

```js
function topoSortBFS(n, edges) {
  const adj = Array.from({ length: n }, () => []);
  const indegree = Array(n).fill(0);

  for (const [u, v] of edges) {
    adj[u].push(v);
    indegree[v]++;
  }

  const queue = [];
  for (let i = 0; i < n; i++) {
    if (indegree[i] === 0) queue.push(i);
  }

  const order = [];
  while (queue.length) {
    const node = queue.shift();
    order.push(node);

    for (const nei of adj[node]) {
      indegree[nei]--;
      if (indegree[nei] === 0) queue.push(nei);
    }
  }

  return order.length === n ? order : [];
}
```

🧠 **Cycle check**
If `order.length !== n` → cycle exists

---

## 5️⃣ Multi-Source BFS (SPREAD / DISTANCE)

![Image](https://blog.tomsawyer.com/hs-fs/hubfs/Blog/2023.09.21.0.CrimeNetwork.Option2_1_optimized_100%20%281%29.png?height=400\&name=2023.09.21.0.CrimeNetwork.Option2_1_optimized_100+%281%29.png\&width=587)

![Image](https://codeforces.com/predownloaded/a5/e9/a5e9c9467ef6b37f122f8b6da0621b54775dc608.png)

### Pattern

* Start BFS from **multiple nodes at once**
* Push all sources into queue initially

---

### Template (Grid)

```js
function multiSourceBFS(grid, sources) {
  const ROWS = grid.length;
  const COLS = grid[0].length;
  const queue = [];

  for (const [r, c] of sources) {
    queue.push([r, c]);
  }

  while (queue.length) {
    const [r, c] = queue.shift();
    for (const [dr, dc] of [[1,0],[-1,0],[0,1],[0,-1]]) {
      const nr = r + dr, nc = c + dc;
      if (nr >= 0 && nc >= 0 && nr < ROWS && nc < COLS && grid[nr][nc] === 0) {
        grid[nr][nc] = 1;
        queue.push([nr, nc]);
      }
    }
  }
}
```

---

### Famous Problems

* Rotting Oranges
* Pacific Atlantic Water Flow
* Nearest Exit from Maze
* Walls & Gates

🧠 **Key idea**
All sources spread **simultaneously**, ensuring minimum distance.

---

## 🧩 Problem → Technique Mapping

| Problem Type               | Technique        |
| -------------------------- | ---------------- |
| Islands / groups           | DFS / BFS        |
| Course schedule            | Cycle detection  |
| Ordering tasks             | Topological sort |
| Shortest path (unweighted) | BFS              |
| Spread / time              | Multi-source BFS |

---

## 📅 3-Day Crash Study Plan

### Day 1

* DFS & BFS templates
* Connected components
* Number of Islands

### Day 2

* Cycle detection (directed + undirected)
* Course Schedule

### Day 3

* Topological Sort (BFS)
* Multi-source BFS problems

---

## 🎯 Interview Tips (VERY IMPORTANT)

* Always **draw the graph**
* Say **why DFS or BFS**
* Mention **time complexity**

  * Graph traversal → `O(V + E)`
* Explain **state tracking** clearly

---








