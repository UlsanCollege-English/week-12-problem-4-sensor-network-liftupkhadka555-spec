[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/0Z1U08Sg)
# hw04 – Minimum Spanning Tree for Sensor Network

## Story

You are helping set up a **sensor network** in a greenhouse complex.  
Each greenhouse is a node. You can place **cables** between greenhouses.  
Each cable has a **cost** (for example, length or price).

You want to connect **all greenhouses** so that:

- Every greenhouse can reach the network.
- The **total cable cost is minimum**.
- There are **no cycles** (no wasted loops).

This is a **Minimum Spanning Tree (MST)** problem.  
We will use a simple **Prim-style** algorithm.

---

## Task

Write a function:

```python
prim_mst(graph, start)
```

- `graph`: dictionary `node -> list of (neighbor, weight)`

    - Assume the graph is undirected: if `A` connects to `B`, then `B` connects to `A`.

    - `weight` is a positive integer cost.

- `start`: starting node for Prim’s algorithm.

Return:

- `(mst_edges, total_cost)` where:

        - `mst_edges` is a list of edges `(u, v, w)` included in the MST.

        - `total_cost` is the sum of all `w` in `mst_edges`.

You may assume for tests:

- `graph` is connected.

- `start` is a valid key in `graph`.

Constraints

- At most 200 nodes.

- All weights are positive integers.

- You may use a simple `list` for candidate edges and sort it.

- Expected time complexity: about O(E²) for this simple version (fine for small graphs).

---

## 8 Steps of Coding – Scaffold (hw04)

For hw04, prompts are minimal. You should drive all steps:

- Step 1: Write (briefly) what MST means in your own words.

- Step 2: Re-phrase the problem: “Connect all nodes with minimum total cost and no cycles.”

- Step 3: Decide inputs/outputs and the structures you will need (`visited`, `edges`, `mst_edges`, `total_cost`).
- Step 4–8: Plan Prim’s algorithm, write pseudocode, code it, debug, and think about performance.

---

## Hints
1. Keep a visited set with nodes already in the tree.

1. Keep a list of candidate edges as (weight, u, v). Always pick the smallest weight edge that connects to a new node.

1. Skip edges where the target node is already in visited. This avoids cycles.

---

## How to Run Tests

```python -m pytest -q```

---

## FAQ

Q1: Do I need to check if the graph is connected?
A1: For this homework, tests assume the graph is connected. You may still think about what happens if it is not.

Q2: Do I have to use a heap?
A2: No. A simple list of edges plus `sort()` is OK.

Q3: What should the MST look like for `n` nodes?
A3: It should have exactly `n - 1` edges if the graph is connected.

Q4: Does MST give shortest path between two nodes?
A4: No. MST connects all nodes cheaply, but does not optimize one specific pair.

Q5: How do I compare edges in tests?
A5: The tests will ignore edge order and treat `(u, v)` same as `(v, u)`.

Q6: What Big-O should I expect?
A6: With a list and sort each time, about O(E²) is fine for small graphs.

Q7: How are mistakes usually made?
A7: Forgetting to check `visited`, or not adding new edges when a node joins the tree.