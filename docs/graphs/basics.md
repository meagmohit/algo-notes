---
layout: default
title: Graph Basics
parent: Graphs
nav_order: 2

---

# Graphs
{: .no_toc }

#### Table of contents
{: .no_toc }

1. TOC
{:toc}

**Graph:** `G = (V, E)`, where for graph `G`, `V` is a set of vertices, and `E` is a set of edges. Every edge `E` is a tuple `(v, w)` where `v, w` $\in$ `V`

**Subgraph:** A subgraph `s` is a set of edges `e` and vertices `v` such that $e \in E$ and $v \in V$

 **Representation:** Adjacency Matrix and Adjacency List



## Detecting Cycles in a Directed Graph
Use DFS and maintain a stack of nodes, if a visited node is present in the stack, cycle detected. [[Leetcode #207]](https://leetcode.com/problems/course-schedule/)

**Time Complexity:** O(V+E) **Space Complexity:**O(V)

```python
def DFS(visited, i, stack)
    visited[i], stack[i] = True, True
    for j in adj[i]:
        if not visited[i]:
            if DFS(visited, j, stack): return True
        elif stack[j]: return True
    stack[j]=False
    return False
def detectCycle(V, adj):
    visited, stack = [False]*V, [False]*V
    for i in range(V):
        if not visited[i]:
            if DFS(visited, i, stack): return True
    return False
```

## Detecting Cycles in an Undirected Graph

Use DFS and a cycle is present if an adjacent vertex is already visited and is not the parent of
the current vertex 

**Time Complexity:** O(V+E) **Space Complexity:**O(V)

```python
def DFS(visited, i, parent)
    visited[i] = True
    for j in adj[i]:
        if not visited[i]:
            if DFS(visited, j, i): return True
        elif parent!=j: return True
    return False
def detectCycle(V, adj):
    visited = [False]*V
    for i in range(V):
        if not visited[i]:
            if DFS(visited, i, -1): return True
    return False
```



# References

- [Runstone Academy PythonDS Book Chapter 8: Graphs](https://runestone.academy/ns/books/published/pythonds/Graphs/toctree.html)
- [Detect Cycles in a directed graph](https://www.geeksforgeeks.org/detect-cycle-in-a-graph/)
- [Detect Cycles in an undirected graph](https://www.geeksforgeeks.org/detect-cycle-undirected-graph/)