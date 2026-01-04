# Graph Problems - Interview Guide

## Problem Index

| Problem | Difficulty | Key Concepts | Status |
|---------|-----------|--------------|--------|
| [Number of Islands](#number-of-islands) | Medium | DFS, Connected Components, Grid Traversal | ✅ |
| Content Cell | | | |
| Content Cell | | | |

***

## Number of Islands

### Problem Overview

Given a 2D grid of `'1'`s (land) and `'0'`s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically.

**Perfect. You already have Google-quality code.**

Now I'll explain it **slowly, mechanically, and intuitively** so you can **re-implement it from scratch** without memorizing.

***

### Visual Understanding (IMPORTANT)







Imagine:
- `'1'` = land
- `'0'` = water

An **island** is just land cells touching **up / down / left / right**.

Your job is **not** to find shapes. Your job is simply to **count how many times you start sinking land**.

***

### Step 0️⃣ — What problem are we really solving?

Forget the grid for a second.

You are solving:

> "How many **connected components** of land exist?"

That's it. Everything else is implementation.

***

### Step 1️⃣ — Why do we even need DFS?

Because:
- When we see **one land cell**, we must **remove all land connected to it**
- Otherwise we'll count the same island multiple times

DFS's job is **NOT to count islands**. DFS's job is to **destroy one island completely**.

***

### Step 2️⃣ — Outer loops: "Scanning the map"

```js
for (let r = 0; r < rows; r++) {
    for (let c = 0; c < cols; c++) {
```

Think like this:

> "I'm walking cell by cell across the map."

Nothing smart yet. Just scanning.

***

### Step 3️⃣ — This is the ONLY moment we count an island

```js
if (grid[r][c] === '1') {
    islands++;
    dfs(r, c);
}
```

### Why do we increment here?

Because:
- This is the **first time** we touched this island
- Everything connected to it hasn't been visited yet

💡 **Key mental rule**

> "Every time I find fresh land, I've discovered a new island."

Then immediately:

> "Let me destroy it so I never see it again."

***

### Step 4️⃣ — What does `dfs(r, c)` REALLY mean?

Forget recursion for a moment.

### `dfs(r, c)` means:

> "From this land cell, sink **everything connected** to it."

That's it.

***

### Step 5️⃣ — The base condition (most important part)

```js
if (
    r < 0 || c < 0 ||
    r >= rows || c >= cols ||
    grid[r][c] === '0'
) return;
```

### This says:

Stop DFS if:
- You fall **outside the grid**
- You hit **water**
- You hit **already visited land** (because we convert land → water)

This prevents:
- Infinite recursion
- Revisiting same cells

***

### Step 6️⃣ — Marking visited (THIS is the trick)

```js
grid[r][c] = '0';
```

Instead of using a `visited` array, we:
- **Sink the land**
- Convert `'1'` → `'0'`

### Why this is genius (and Google loves it):
- Saves space
- Simpler code
- Less bugs
- Clear intent

Once sunk, that land **can never be counted again**.

***

### Step 7️⃣ — Exploring neighbors

```js
dfs(r + 1, c);
dfs(r - 1, c);
dfs(r, c + 1);
dfs(r, c - 1);
```

This means:

> "From this land cell, walk in all 4 directions."

Each call either:
- Sinks land
- Or immediately returns (if water/outside)

DFS naturally spreads until the whole island is gone.

***

### Step 8️⃣ — Why this works (the invariant)

After `dfs(r, c)` finishes:
- **The entire island is erased**
- No cell of that island will ever trigger `islands++` again

That's the invariant Google interviewers care about.

***

### Step 9️⃣ — How YOU implement this from scratch (no memorization)

### Write it in THIS order every time:

1. Loop through grid
2. If cell is land:
   - Increment island count
   - Call DFS
3. DFS:
   - Boundary check
   - Water check
   - Mark visited
   - Explore neighbors

If you follow this order, you'll never get stuck.

***

### Step 🔟 — What prerequisites you ACTUALLY need (Noogler path)

Forget 100 topics. You need **just these**:

### ✅ Must-know concepts

1. **Recursion basics**
   - Function calling itself
   - Base condition
2. **Grid traversal**
   - Row / column movement
3. **Connected components**
   - One start → many reachable nodes
4. **DFS vs BFS (conceptual only)**

That's it.

***

### What you do NOT need

- ❌ Graph theory textbooks
- ❌ Fancy math
- ❌ Union-Find
- ❌ Dynamic Programming

***

### Google Interview Checklist (print this mentally)

Before coding, say out loud:

> "This is a connected components problem. I'll use DFS to flood-fill each island."

While coding:
- Boundary check first
- Mark visited early
- Explore all directions

After coding:

> "Time complexity is O(rows × cols). Space is recursion stack worst case O(rows × cols)."

You sound like a Noogler already.

***

### Final truth (important)

Google does **not** expect brilliance. They expect **clarity + correctness**.

If you can:
- Explain this in your own words
- Re-implement without copying
- Handle edge cases calmly

👉 You're hireable.

***

## Follow-Up Questions

Below are **REAL Google-style follow-up questions** you'll get *after* you finish `Number of Islands`. These are not trick questions — they test **depth, clarity, and calm thinking**.

### 🧠 Level 1 — Clarification & Edge Cases

| Question | Jump to Answer |
|----------|---------------|
| What happens if the grid is empty? | [Answer](#q1-empty-grid) |
| What if the grid is all water? | [Answer](#q2-all-water) |
| What if the grid is all land? | [Answer](#q3-all-land) |

### 🧠 Level 2 — Complexity

| Question | Jump to Answer |
|----------|---------------|
| What is the time complexity? | [Answer](#q4-time-complexity) |
| What is the space complexity? | [Answer](#q5-space-complexity) |

### 🧠 Level 3 — DFS vs BFS

| Question | Jump to Answer |
|----------|---------------|
| Can you solve this using BFS? | [Answer](#q6-bfs-solution) |
| Why did you choose DFS over BFS? | [Answer](#q7-dfs-choice) |

### 🧠 Level 4 — Design & Constraints

| Question | Jump to Answer |
|----------|---------------|
| What if recursion depth is too large? | [Answer](#q8-recursion-depth) |
| What if we are not allowed to modify the grid? | [Answer](#q9-immutable-grid) |

### 🧠 Level 5 — Variations

| Question | Jump to Answer |
|----------|---------------|
| What if diagonal connections are allowed? | [Answer](#q10-diagonal) |
| What if the grid is extremely large and stored on disk? | [Answer](#q11-large-grid) |
| Can you count the size of each island? | [Answer](#q12-island-size) |

### 🧠 Level 6 — Theory Check

| Question | Jump to Answer |
|----------|---------------|
| What is this problem an example of? | [Answer](#q13-problem-type) |
| Why does DFS not revisit cells? | [Answer](#q14-no-revisit) |

### 🧠 Level 7 — Advanced

| Question | Jump to Answer |
|----------|---------------|
| Could Union-Find be used? | [Answer](#q15-union-find) |
| How would you parallelize this? | [Answer](#q16-parallelize) |

***

## Detailed Answers

### <a name="q1-empty-grid"></a>Q1: What happens if the grid is empty?

**Good answer**

> "I handle that upfront by returning 0 if the grid is empty."

**Bad answer**

> "It won't happen."

[Back to questions](#-level-1--clarification--edge-cases)

***

### <a name="q2-all-water"></a>Q2: What if the grid is all water?

**Good**

> "DFS is never called, so island count stays 0."

[Back to questions](#-level-1--clarification--edge-cases)

***

### <a name="q3-all-land"></a>Q3: What if the grid is all land?

**Good**

> "DFS runs once and marks the entire grid visited, so result is 1."

[Back to questions](#-level-1--clarification--edge-cases)

***

### <a name="q4-time-complexity"></a>Q4: What is the time complexity?

**Correct**

> "O(rows × cols) because each cell is visited at most once."

[Back to questions](#-level-2--complexity)

***

### <a name="q5-space-complexity"></a>Q5: What is the space complexity?

**Correct**

> "Worst case O(rows × cols) due to recursion stack."

🔴 **Don't say**: "O(1)" — that's wrong.

[Back to questions](#-level-2--complexity)

***

### <a name="q6-bfs-solution"></a>Q6: Can you solve this using BFS?

**Perfect Google answer**

> "Yes. BFS also works since this is a connected components problem. DFS and BFS are interchangeable here."

🚀 Short. Confident. Done.

[Back to questions](#-level-3--dfs-vs-bfs)

***

### <a name="q7-dfs-choice"></a>Q7: Why did you choose DFS over BFS?

**Best**

> "DFS is simpler to implement for flood-fill problems and easier to reason about here."

[Back to questions](#-level-3--dfs-vs-bfs)

***

### <a name="q8-recursion-depth"></a>Q8: What if recursion depth is too large?

**Strong**

> "We can convert DFS to iterative using an explicit stack, or use BFS."

(They're checking awareness, not implementation.)

[Back to questions](#-level-4--design--constraints)

***

### <a name="q9-immutable-grid"></a>Q9: What if we are not allowed to modify the grid?

**Correct**

> "I would use a separate visited boolean matrix."

[Back to questions](#-level-4--design--constraints)

***

### <a name="q10-diagonal"></a>Q10: What if diagonal connections are allowed?

**Answer**

> "I would add 4 more directions to DFS."

This tests adaptability.

[Back to questions](#-level-5--variations)

***

### <a name="q11-large-grid"></a>Q11: What if the grid is extremely large and stored on disk?

**Good**

> "We'd need chunk-based processing or Union-Find with streaming, since recursion wouldn't scale."

(They don't expect code.)

[Back to questions](#-level-5--variations)

***

### <a name="q12-island-size"></a>Q12: Can you count the size of each island?

**Good**

> "Yes. DFS can return a count for each island."

[Back to questions](#-level-5--variations)

***

### <a name="q13-problem-type"></a>Q13: What is this problem an example of?

**Correct**

> "Connected components in an undirected graph."

[Back to questions](#-level-6--theory-check)

***

### <a name="q14-no-revisit"></a>Q14: Why does DFS not revisit cells?

**Correct**

> "Because we mark cells visited immediately."

[Back to questions](#-level-6--theory-check)

***

### <a name="q15-union-find"></a>Q15: Could Union-Find be used?

**Perfect**

> "Yes, but it's overkill. DFS is simpler and more space-efficient."

[Back to questions](#-level-7--advanced)

***

### <a name="q16-parallelize"></a>Q16: How would you parallelize this?

**Advanced**

> "We could process independent regions in parallel, but merging connected components would require synchronization."

(They're checking thinking, not solution.)

[Back to questions](#-level-7--advanced)

***

## Interview Responses Guide

### ❌ Answers that FAIL candidates

- 🚫 "Because I memorized this solution"
- 🚫 "LeetCode says to use DFS"
- 🚫 "I don't know, it just works"

### ✅ Answers that PASS candidates

- ✔ "This is a connected components problem"
- ✔ "DFS floods the island completely"
- ✔ "Each cell is visited once"
- ✔ "Edge cases are handled"

***

## 🧢 Noogler Interview Golden Script

**Memorize this:**

> "This is a connected components problem on a grid. I iterate through the grid, and when I find unvisited land, I increment the island count and run DFS to mark all connected land as visited."

If you say that calmly — **you are in the top tier**.
