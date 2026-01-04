Yes — **Graph problems are extremely pattern-driven**, and at **Google SDE-3** the real test is **recognition + correct abstraction**, not just writing BFS/DFS.

Interviewers expect you to **map the problem to a known graph pattern in under 60 seconds**, explain **why that traversal/algorithm fits**, and discuss **trade-offs**.

Below is the **Google SDE-3 Graph Playbook**.

---

# 🧠 Graph Problem Patterns (Google SDE-3 Mental Model)

## 🔑 Universal Graph Checklist (Say This First)

Before coding, say out loud:

1. **What are nodes and edges?**
2. **Is the graph directed or undirected?**
3. **Is it weighted or unweighted?**
4. **Do I need shortest path, connectivity, or ordering?**
5. **Is this static or dynamic traversal?**

If you answer these → the pattern becomes obvious.

---

## 1️⃣ **Connected Components / Traversal Pattern**

> “How many separate groups exist?”

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20220905132251/graph.jpg)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240216084522/bfs-vs-dfs-%281%29.png)

### Used When

* Count islands / networks
* Detect isolated groups
* Simple reachability

### Technique

* DFS or BFS
* Visited set

### Classic Problems

* Number of Islands
* Number of Connected Components
* Friend Circles

🟢 **Google Follow-up**

> “DFS vs BFS — which and why?”

---

## 2️⃣ **Cycle Detection Pattern**

> “Can I revisit a node illegally?”

![Image](https://media.geeksforgeeks.org/wp-content/uploads/cycle-BFS.png)

![Image](https://favtutor.com/resources/images/uploads/Detect_cycle_in_an_undirected_graph.png)

### Two Variants

| Graph Type | Technique                 |
| ---------- | ------------------------- |
| Undirected | Parent tracking           |
| Directed   | Recursion stack (3-color) |

### Classic Problems

* Course Schedule
* Detect Cycle in Graph

### Key Insight

Cycle = **invalid dependency**

🟢 **Google Follow-up**

> “Why is visited alone insufficient for directed graphs?”

---

## 3️⃣ **Topological Sort / Dependency Pattern**

> “What order must things happen?”

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AuMg_ojFXts2WZSjcZe4oRQ.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2A4fxydkQcnOQETpefYMq4VQ.png)

### Used When

* Prerequisites
* Build systems
* Dependency resolution

### Techniques

* DFS + stack
* Kahn’s BFS (indegree)

### Classic Problems

* Course Schedule II
* Alien Dictionary

🟢 **Google Follow-up**

> “How do you detect cycles during topo sort?”

---

## 4️⃣ **Shortest Path Pattern**

> “Minimum cost / steps to reach”

![Image](https://www.researchgate.net/publication/382193848/figure/fig4/AS%3A11431281260077625%401720804178334/Dijkstra-algorithm-visualization-Weights-of-edges-are-written-on-them-Numbers-on.jpg)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/Graph_for_multi_sorce_bfs-1-300x166.png)

### Decision Table

| Graph               | Algorithm    |
| ------------------- | ------------ |
| Unweighted          | BFS          |
| Weighted (positive) | Dijkstra     |
| Negative weights    | Bellman-Ford |

### Classic Problems

* Shortest Path in Binary Matrix
* Network Delay Time

🟢 **Google Follow-up**

> “Why BFS fails with weighted edges?”

---

## 5️⃣ **Multi-Source BFS Pattern**

> “Distance from multiple starting points”

![Image](https://miro.medium.com/v2/resize%3Afit%3A1000/1%2A9SEOUHfqLnWwXisGUuuFBg.gif)

![Image](https://assets.leetcode.com/uploads/2019/02/16/oranges.png)

### Used When

* Spread simulation
* Nearest distance
* Time propagation

### Trick

👉 Push **all sources first**

### Classic Problems

* Rotting Oranges
* Walls and Gates

🟢 **Google Follow-up**

> “Why is this still O(n)?”

---

## 6️⃣ **Grid as Graph Pattern**

> “Matrix = graph in disguise”

![Image](https://miro.medium.com/1%2Ajm2boSpZ70lqy9_qY8CowQ.png)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240424142803/Adjacency-Matrix-for-Directed-and-Unweighted-graph.webp)

### Used When

* 2D matrices
* Movement in directions

### Technique

* DFS/BFS + directions array

### Classic Problems

* Pacific Atlantic Water Flow
* Word Search

🟢 **Google Follow-up**

> “Why do we mutate grid instead of visited array?”

---

## 7️⃣ **Union-Find / Disjoint Set Pattern**

> “Dynamic connectivity”

![Image](https://he-s3.s3.amazonaws.com/media/uploads/a1f5858.jpg)

![Image](https://tutorialhorizon.com/static/media/algorithms/2015/06/find-union-5.png)

### Used When

* Edges added dynamically
* Need fast connectivity checks

### Classic Problems

* Graph Valid Tree
* Redundant Connection

### Complexity

Almost O(1) with path compression

🟢 **Google Follow-up**

> “Why Union-Find can’t detect directed cycles?”

---

## 8️⃣ **Minimum Spanning Tree (MST) Pattern**

> “Connect all nodes cheaply”

![Image](https://s3.amazonaws.com/learneroo-images/main/Minimum_spanning_tree.png)

![Image](https://i.sstatic.net/KofyW.gif)

### Algorithms

* Kruskal → Union-Find
* Prim → Heap

### Classic Problems

* Min Cost to Connect All Points

🟢 **Google Follow-up**

> “Kruskal vs Prim — when to use which?”

---

## 9️⃣ **State Graph / BFS on State Space**

> “Nodes are states, not values”

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240430142639/bfs.webp)

![Image](https://runestone.academy/ns/books/published/javads/external/Graphs/Figures/wordgraph.png)

### Used When

* Transformations
* Each step changes state

### Classic Problems

* Word Ladder
* Open the Lock

🟢 **Google Follow-up**

> “Why is visited critical here?”

---

## 🧩 Graph Pattern Recognition Table

| Problem Mentions…     | Pattern              |
| --------------------- | -------------------- |
| “Groups / islands”    | Connected components |
| “Prerequisites”       | Topological sort     |
| “Cycle / impossible”  | Cycle detection      |
| “Minimum steps”       | BFS                  |
| “Minimum cost”        | Dijkstra / MST       |
| “Grid / matrix”       | Graph traversal      |
| “Dynamic connections” | Union-Find           |
| “Transformations”     | State graph          |

---

## 🧠 Google SDE-3 Expectations (VERY IMPORTANT)

They test:

| Skill            | What They Look For           |
| ---------------- | ---------------------------- |
| Modeling         | Correct node/edge definition |
| Algorithm choice | BFS vs DFS vs Heap           |
| Complexity       | Why this is optimal          |
| Trade-offs       | Alternative approaches       |
| Clarity          | Clean traversal logic        |

---

## 🎯 Interview Power Sentence (USE THIS)

Say this early:

> “I’ll model this as a graph where nodes represent X and edges represent Y. Since the graph is unweighted and I need shortest steps, BFS is optimal.”

This **instantly signals seniority**.

---

=====================================================

Perfect choice. **Graphs are one of Google’s strongest SDE-3 signal areas** because they test *modeling skill, algorithm selection, and reasoning under constraints*.

Below is a **15-day Graph Mastery Plan** built for **Google SDE-3 interviews**, assuming you already know basic BFS/DFS.

⏱ **Time**: ~1–1.5 hrs/day
🎯 **Outcome**: You’ll map problems to the **correct graph pattern in < 60 seconds**, justify the algorithm, and handle follow-ups confidently.

---

# 🧠 15-Day Graph Mastery Plan (Google SDE-3)

---

## 🔑 Daily Non-Negotiables (Say These Out Loud)

Before coding **every day**:

1. What are the **nodes**?
2. What are the **edges**?
3. Directed or undirected?
4. Weighted or unweighted?
5. What is the **exact goal** (connectivity, order, shortest path, cost)?

If you can’t answer → stop and re-model.

---

## 📅 WEEK 1 — Graph Foundations & Core Patterns

---

## **Day 1 – Graph Modeling (MOST IMPORTANT DAY)**

🎯 Goal: Translate any problem into a graph

### Learn

* Adjacency list vs matrix
* Implicit graphs (grids, strings, states)
* When *not* to build an explicit graph

### Practice

* Number of Islands (grid → graph)
* Clone Graph

🟢 Google Follow-up

> “What exactly is a node here? Why not something else?”

---

## **Day 2 – DFS vs BFS (Traversal Mastery)**

🎯 Goal: Pick traversal *with reason*

![Image](https://deen3evddmddt.cloudfront.net/uploads/content-images/bfs-vs-dfs.webp)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240216084522/bfs-vs-dfs-%281%29.png)

### Practice

* Flood Fill
* Max Area of Island

### Focus

* Stack vs queue
* Recursion depth vs memory

🟢 Google Follow-up

> “When would DFS cause stack overflow? How to fix?”

---

## **Day 3 – Connected Components Pattern**

🎯 Goal: Count independent groups

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20220905132251/graph.jpg)

![Image](https://cdn.programiz.com/sites/tutorial2program/files/scc-strongly-connected-components.png)

### Practice

* Number of Connected Components
* Friend Circles

### Key Insight

Each DFS/BFS call = **one component**

🟢 Google Follow-up

> “How would this change if the graph was directed?”

---

## **Day 4 – Cycle Detection (Directed vs Undirected)**

🎯 Goal: Spot impossible states

![Image](https://media.geeksforgeeks.org/wp-content/uploads/cycle-BFS.png)

![Image](https://favtutor.com/resources/images/uploads/Detect_cycle_in_an_undirected_graph.png)

### Practice

* Course Schedule
* Detect Cycle in Graph

### Focus

* Parent tracking (undirected)
* 3-color DFS (directed)

🟢 Google Follow-up

> “Why isn’t visited[] enough for directed graphs?”

---

## **Day 5 – Review + Speed Day**

🎯 Goal: Pattern recognition

### Drill

* 5 problems → identify pattern in < 1 min
* Explain algorithm choice before coding

---

## 📅 WEEK 2 — Ordering, Distance & Constraints

---

## **Day 6 – Topological Sort (Dependencies)**

🎯 Goal: Ordering with constraints

![Image](https://iq.opengenus.org/content/images/2020/03/topo1-1.png)

![Image](https://i.imgur.com/Q3MA6dZ.png)

### Practice

* Course Schedule II
* Alien Dictionary

### Focus

* DFS topo vs Kahn’s BFS
* Cycle detection during topo

🟢 Google Follow-up

> “How do you detect cycles while sorting?”

---

## **Day 7 – BFS for Shortest Path (Unweighted)**

🎯 Goal: Minimum steps

![Image](https://media.geeksforgeeks.org/wp-content/uploads/Graph_for_multi_sorce_bfs-1-300x166.png)

![Image](https://files.codingninjas.in/binary-matrix-5821.png)

### Practice

* Shortest Path in Binary Matrix
* Word Ladder (intro)

### Focus

* Level-by-level traversal
* Distance tracking

🟢 Google Follow-up

> “Why is BFS optimal here?”

---

## **Day 8 – Dijkstra (Weighted Graphs)**

🎯 Goal: Cost-based traversal

![Image](https://www.researchgate.net/publication/382193848/figure/fig4/AS%3A11431281260077625%401720804178334/Dijkstra-algorithm-visualization-Weights-of-edges-are-written-on-them-Numbers-on.jpg)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20190912131458/widestpath6.png)

### Practice

* Network Delay Time
* Path With Minimum Effort

### Focus

* Priority queue invariant
* Why nodes enter heap multiple times

🟢 Google Follow-up

> “Why doesn’t BFS work with weights?”

---

## **Day 9 – Multi-Source BFS**

🎯 Goal: Spread / influence problems

![Image](https://miro.medium.com/v2/resize%3Afit%3A1000/1%2A9SEOUHfqLnWwXisGUuuFBg.gif)

![Image](https://assets.leetcode.com/uploads/2019/02/16/oranges.png)

### Practice

* Rotting Oranges
* Walls and Gates

### Key Trick

Push **all sources first**

🟢 Google Follow-up

> “Why is this still O(N)?”

---

## **Day 10 – Grid as Graph (Advanced)**

🎯 Goal: Treat matrices like graphs naturally

![Image](https://miro.medium.com/1%2Ajm2boSpZ70lqy9_qY8CowQ.png)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240424142803/Adjacency-Matrix-for-Directed-and-Unweighted-graph.webp)

### Practice

* Pacific Atlantic Water Flow
* Word Search

### Focus

* Direction arrays
* Mark & rollback patterns

🟢 Google Follow-up

> “Why mutate grid instead of visited array?”

---

## 📅 WEEK 3 — Advanced Graph Patterns (Google SDE-3)

---

## **Day 11 – Union-Find (Dynamic Connectivity)**

🎯 Goal: Fast connectivity checks

![Image](https://he-s3.s3.amazonaws.com/media/uploads/a1f5858.jpg)

![Image](https://cp-algorithms.com/data_structures/DSU_path_compression.png)

### Practice

* Graph Valid Tree
* Redundant Connection

### Focus

* Path compression
* Union by rank

🟢 Google Follow-up

> “Why can’t Union-Find detect directed cycles?”

---

## **Day 12 – Minimum Spanning Tree (MST)**

🎯 Goal: Connect cheaply

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20250225154939293361/Prims-Algorithm-1.webp)

![Image](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d2/Minimum_spanning_tree.svg/1200px-Minimum_spanning_tree.svg.png)

### Practice

* Min Cost to Connect All Points

### Focus

* Kruskal vs Prim
* Heap vs Union-Find tradeoff

🟢 Google Follow-up

> “Which algorithm works better for dense graphs?”

---

## **Day 13 – State Space Graphs**

🎯 Goal: Think beyond nodes as numbers

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240430142639/bfs.webp)

![Image](https://runestone.academy/ns/books/published/javads/external/Graphs/Figures/wordgraph.png)

### Practice

* Word Ladder
* Open the Lock

### Focus

* State encoding
* Explosion control via visited

🟢 Google Follow-up

> “What causes state explosion? How do you prune?”

---

## **Day 14 – Hard Graph Problems**

🎯 Goal: Confidence under complexity

### Practice

* Critical Connections (Bridges)
* Accounts Merge

### Focus

* Discovery time
* Graph compression

🟢 Google Follow-up

> “Why does this edge matter?”

---

## **Day 15 – Final Google Readiness Check**

🎯 Goal: Interview-ready clarity

### You must confidently say:

> “I’ll model this as a graph with X as nodes and Y as edges. Since it’s unweighted and I need shortest steps, BFS is optimal with O(V + E) complexity.”

### Final Checklist

✔ Pattern recognition < 60 sec
✔ Correct algorithm choice
✔ Clear invariants
✔ Clean, iterative JS code

---

## 🏆 Outcome After 15 Days

You will:

* Instantly classify **any graph problem**
* Choose BFS / DFS / Dijkstra / Union-Find confidently
* Explain trade-offs like a senior engineer
* Handle Google SDE-3 follow-ups calmly

---
