---
layout: default
title: Minimum Spanning Tree
nav_order: 5
---

# Minimum Spanning Tree

A **spanning tree** is a connected subgraph in an undirected graph where all vertices are connected with minimum number of edges. **Minimum Spanning Tree** is a spanning tree with minimum possible total edge weight in a *weighted undirected graph*.

**Cut Property**

- A cut is a partition of subgraph with two disjoint subsets (disjoint subsets refer that vertices inside each subset are connected, but there is no edge from one subset to another). For a graph $G = (V, E)$, a cut $C = (S, T)$ is a partition of $V$.
- Any cut determines the cut-set, a set of edges that have one endpoint in each subset of the partition [2]. These edges are said to cross the cut, or crossing edges. The cut-set of the cut $C = (S, T)$ is the set $\{(u,v) \in E | u\in S, v\in T\}$
- Cut Property: For any cut $C$ of the graph, if the weight of an edge $E$ in the cut-set of $C$ is strictly smaller than all other edges of cut-set $C$, then this edge belongs to all the MSTs of the Graph.

**Minimum weight spanning tree:** Formally we define the minimum spanning tree $𝑇$ for a graph $𝐺=(𝑉,𝐸)$ as follows. $𝑇$ is an acyclic subset of $𝐸$ that connects all the vertices in $𝑉$. The sum of the weights of the edges in $T$ is minimized.



## Kruskal Algorithm

Sort all the edges based on their weight, and keep adding the order if it doesn’t form a cycle.



## Prim's Algorithm

For the vertices who are present in MST, check which edge has the minimum weight to the vertex who is not present in MST (i.e., will not create cycle), and add it.



### Complexity Analysis

| Algorithm | Time Complexity                                     | Space Complexity |
| --------- | --------------------------------------------------- | ---------------- |
| Kruskal   | O(ElogE)                                            | O(V) + sorting   |
| Prim      | O(E.logV) for binary heap O(E+V.logV) for fibonacci | O(V)             |



{: .note }
Both Kruskal and Prim are greedy algorithms

