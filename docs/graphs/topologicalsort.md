---
layout: default
title: Topological Sorting
parent: Graphs
nav_order: 6
---



# Topological Sorting

A topological sort takes a directed acyclic graph and produces a linear ordering of all its vertices such that if the graph 𝐺 contains an edge (𝑣,𝑤) then the vertex 𝑣 comes before the vertex 𝑤 in the ordering.



### Algorithm

1. Call `dfs(g)` for some graph `g`. The main reason we want to call depth first search is to compute the finish times for each of the vertices.
2. Store the vertices in a list in decreasing order of finish time.
3. Return the ordered list as the result of the topological sort



## Kahn's Algorithm for Topological Sorting

Maintain a queue of vertex which have inDegree as 0. While iterating over the queue, if the connected vertex now has 0 inDegree add it to the queue.

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



