---
layout: default
title: DFS
parent: Algorithms
nav_order: 3

---

# **Depth-First Search (DFS)**



##  DFS Template using Recursion

- The nodes we visit earlier might not be nodes closer to the root node 

- **Time Complexity:** O(V+E), **Space Complexity:** O(V)

```python
visited = {}
def DFS(node, g): # assume g[node] is a list of connected nodes (Adjacency List)
    visited[node] = True
    for nei in g[node]:
        if nei not in visited:
            DFS(nei, g)
```

**Questions:** [[Leetcode #200]](https://leetcode.com/problems/number-of-islands/)

{: .note}
If the depth of recursion is too high, it will lead to `stack overflow`. In that case, it is advisable to use either BFS or DFS using an explicit stack





## DFS with Explicit Stacks

- Add or remove items to stack as per the requirements of the results

```python
def DFS(src, g): # g is graph in adjacency list format
	stack = [src]
	visited = set()
	while stack:
		node = stack.pop()
		if node not in visited:
			visited.add(node)
			for nei in g[node]:
				if nei not in visited: stack.append(nei)
				
```



**Questions:** [[Leetcode #94]](https://leetcode.com/problems/binary-tree-inorder-traversal/)

 

