---
layout: default
title: Single-Source Shortest Path Algorithms
nav_order: 4
---



# Single-Source Shortest Path Algorithms

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

Given the starting vertex, can you find the shortest path to any of the vertices in a **weighted** graph

**Edge Relaxation:** In cases, when there are multiple paths from vertex $u$ to vertex $v$, if $d[u]+w(u,v) < d[v]$ , we update $d[v]$ to be $d[u]+w(u,v)$. This is equivalent to tightening the edge with minimum weight such that the edge with higher weights is relaxed.



## Dijakstra Algorithm

Greedy approach, for graphs with only non-negative edges to determine the shortest path between source vertex to all other vertices 

**Note:** We might have the same node multiple times in the heapq, however, the entry with minimum distance will be visited earlier.

**Time Complexity:** O(E + VlogV) for Fibonacci heaps, and O(V + ElogV) for binary heaps. Generally, it is considered O((V+E).log(V+E))

**Space Complexity:** O(V)

```python
def dijakstra(g, src, n): # Graph g with vertex src and total n vertices
	dist, visited = [float("inf")]*n, [False]*n
	heap = heapq([[0, src]])
	dist[src] = 0
	while q:
		_, u = heapq.heappop(heap)
		if visited[u]: continue
		visited[u] = True
		for (v, w) in g[u]:
			if dist[u] + w < dist[v]:
				dist[v]	= dist[u] + w
				heapq.hepapush(heap, [dist[v], v])
```



## **Bellman-Ford Algorithm**

Uses DP-like technique, works for graphs with negative edges, to find the shortest path between source vertex to all other vertices. [1]

**Theorem 1:** In a “graph with no negative weight cycles” with N vertices, the shortest path between any two vertices has at most N-1 edges

**Theorem 2:** In a “graph with negative weight cycles”, there is no shortest path

Note: If the weight keeps reducing after N-1 iterations, it means that the graph has negative weight cycles

Optimization 1: Can use 1-D DP array to reduce space-complexity to O(V)

Optimization 2: Can stop early, with in-place replacements if there is no change

**Time Complexity:** O(E.V), **Space Complexity:** O(V^2)

```python
# Graph g with vertex src and total n vertices
def bellman_ford(g, src, n): 
	k = n-1 # gives the minimum distance considering only k edges
	dp = [float("inf")]*n for _ in range(k)]
	dp[0][0] = 0
	for i in range(k):
		for u, v, d in g: 
		# u: source vertex, v: dest vertex, d: distance
			dp[i][v] = min(dp[i][v], dp[i-1][u]+d)
```



## Shortest Path Faster Algorithm

In the Bellman-Ford algorithm, if there is an update for vertex v, mark it as “present in the queue” and add it to the queue. If such a vertex already exists, don’t add it to the queue. This will improve the average time complexity but the worst case time-complexity will remain same.