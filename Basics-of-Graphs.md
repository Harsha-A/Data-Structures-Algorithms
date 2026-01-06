Below is a **clean, from-scratch, Noogler-level explanation of Graphs** — exactly what interviewers **expect you to already know** before asking DFS/BFS problems.

No heavy theory. No university jargon. Just **interview-useful fundamentals**.

---

# 🧠 Graph Basics — Noogler DE Interview Level

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
