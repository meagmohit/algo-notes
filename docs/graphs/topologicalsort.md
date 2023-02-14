---
layout: default
title: Topological Sorting
parent: Graphs
nav_order: 6
---

# Topological Sorting
{: .no_toc }

#### Table of contents
{: .no_toc }

1. TOC
{:toc}

A topological sort takes a directed acyclic graph and produces a linear ordering of all its vertices such that if the graph 𝐺 contains an edge (𝑣,𝑤) then the vertex 𝑣 comes before the vertex 𝑤 in the ordering. [[Ref1]](https://www.geeksforgeeks.org/topological-sorting/) [[Ref2]](https://www.techiedelight.com/topological-sorting-dag/)


## DFS-based Topological Sorting
Add to the final stack when finished exploring all the neighbors.

**Time Complexity:** O(V+E), **Space Complexity:** O(V)

```python
def DFS(visited, u, out):
    visited[u] = True
    for v in adj[u]:
        if not visited[u]: DFS(visited, u, out)
    out.append(u)
def TS(V, adj):
    visited, out = [False]*V, []
    for u in range(V):
        if not visited[u]: DFS(visited, u, out)
    return out[::-1]
```



## Kahn's Algorithm for Topological Sorting

Maintain a queue of vertex which have inDegree as 0. While iterating over the queue, if the connected vertex now has 0 inDegree add it to the queue. **Time Complexity:** O(V+E), **Space Complexity:** O(V) [[Ref1]](https://www.geeksforgeeks.org/topological-sorting-indegree-based-solution/) [[Ref2]](https://www.techiedelight.com/kahn-topological-sort-algorithm/)

- Only works with **directed** and **acyclic** graphs
- There must be one vertex in graph with inDegree as 0.

```python
def kahn(n, edges): # assumes n vertices, and edges[u] = [v1, v2] as directed edges
	inDegree, visited, dq = [0]*n, [False]*n, deque()
	for u in edges:
		for v in edges[u]: inDegree[v] += 1
	res = []
	for idx in range(n): 
		if inDegree[idx]==0: dq.append(idx)
	while dq:
		u = dq.popleft()
		visited[u] = True
		res.append(u)
		for v in g[u]:
			if visited[v]: return -1 # cycle
			inDegree[v]-=1 
			if inDegree[v]==0: dq.append(v)
	if len(res) < n: return -1 # all vertice are not included in the result
	return res
	
```

[[Leetcode #210]](https://leetcode.com/problems/course-schedule-ii/)

{: .note}
**Topological sorts on Cyclic Graphs:**
If topological sort outputs more than N vertices - it means there is a cycle



## All Topological Sorts

Use Kahn’s Topological Sorting along with DFS/backtracking. **Time Complexity:** O(V+E), **Space Complexity:** O(V) [[Ref1]](https://www.geeksforgeeks.org/all-topological-sorts-of-a-directed-acyclic-graph/) [[Ref2]](https://www.techiedelight.com/find-all-possible-topological-orderings-of-dag/)

```python
def DFS(visited, indegree, out):
    for u in range(V):
        if indegree[u]==0 and not visited[u]:
            visited[u] = True
            out.append(u)
            for v in adj[u]: indegree[v]-=1
            DFS(visited, indegree, out)
            visited[u] = False
            out.pop()
            for v in adj[u]: indegree[v]+=1
    if len(out)==V: print out

def TS(V, adj):
    visited, out, indegree = [False]*V, [], [0]*V
    for u in range(V):
        for v in adj[u]: indegree[v]+=1
    DFS(visited, indegree, out)
```
[[Leetcode #1136]](https://leetcode.com/problems/parallel-courses/) [[Leetcode #1494]](https://leetcode.com/problems/parallel-courses-ii/)
