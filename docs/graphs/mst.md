---
layout: default
title: Minimum Spanning Tree
parent: Graphs
nav_order: 7
---

# Minimum Spanning Tree

{: .no_toc }

#### Table of contents
{: .no_toc }

1. TOC
{:toc}

A **spanning tree** is a connected subgraph in an undirected graph where all vertices are connected with minimum number of edges. **Minimum Spanning Tree** is a spanning tree with minimum possible total edge weight in a *weighted undirected graph*.

### Cut Property

- A cut is a partition of subgraph with two disjoint subsets (disjoint subsets refer that vertices inside each subset are connected, but there is no edge from one subset to another). For a graph `G = (V, E)`, a cut `C = (S, T)` is a partition of `V`.
- Any cut determines the cut-set, a set of edges that have one endpoint in each subset of the partition. These edges are said to cross the cut, or crossing edges. The cut-set of the cut `C = (S, T)` is the set `{(u,v) \in E | u \in S, v\ in T\}`.
- Cut Property: For any cut `C` of the graph, if the weight of an edge `E` in the cut-set of `C` is strictly smaller than all other edges of cut-set `C`, then this edge belongs to all the MSTs of the Graph.

Formally we define the minimum spanning tree `𝑇` for a graph `𝐺=(𝑉,𝐸)` as follows. `𝑇` is an acyclic subset of `𝐸` that connects all the vertices in `𝑉`. The sum of the weights of the edges in `T` is minimized.



## Kruskal Algorithm

Sort all the edges based on their weight, and keep adding the order if it doesn’t form a cycle.

```python
def kruskal(n, E): #n is number of vertices, E is set of edges with (source, dest, weight)
	uf = UnionFind(n)
	E.sort(key = lambda x:x[2], reverse=True)
	mst = []
	while E and len(mst)<n-1:
		src, dst, weight = E.pop()
		if not connected(src, dst):
			uf.union(src, dst)
			mst.append((src, dst, weight))
	return mst
```

## Prim's Algorithm

For the vertices who are present in MST, check which edge has the minimum weight to the vertex who is not present in MST (i.e., will not create cycle), and add it.

```python
def prim(n, E): # assume here E is dict with E[u] = [[w1, v1], [w2, v2]]
	in_mst = [False]*n # check if the vertex is present in MST
	heap, mst, n_edges = [[0, 0]], [], 0 # addign dummy heap item
	while len(mst) <= n and heap:
		w, v = heapq.heappop(heap)
		if not in_mst[v]:
			in_mst[v], n_edges = True, n_edges+1
			for w2, v2 in E[v]:
				if not in_mst[v2]: 
					heapq.heappush(heap, [w2, v2])
	return mst
```

### Complexity Analysis

| Algorithm | Time Complexity                                     | Space Complexity |
| --------- | --------------------------------------------------- | ---------------- |
| Kruskal   | O(ElogE)                                            | O(V) + sorting   |
| Prim      | O(E.logV) for binary heap O(E+V.logV) for fibonacci | O(V)             |



{: .note }
Both Kruskal and Prim are greedy algorithms

