---
layout: default
title: BFS/DFS
parent: Graphs
nav_order: 3

---

# Graph Search Algorithms
{: .no_toc }

#### Table of contents
{: .no_toc }

1. TOC
{:toc}


# Breadth-First Search (BFS)

## Generic BFS Template

- The nodes closer to the root node will be traversed earlier
- Implemented Using Queues (`deque` module in python)
- **Time Complexity:** O(V+E), **Space Complexity:** O(V)

```python
from collections import deque
def BFS(g): # assume g[node] is a list of connected nodes (Adjacency List)
    dq = deque([[0, root]]) # focus here on list inside list
    visited = {}
    visited[root] = True
    while(len(dq)>0):
        d, node = dq.popleft()
        for nei in g[node]:
            if nei not in visited:
                dq.append([d+1, nei])
                visited[nei] = True
```




<!---
## BFS with Multiple Sources

{: .warning}

TO-DO
--->


## BFS with State

In a few cases, we need to consider additional state variables while exploring via BFS. In such scenarios use the additional state variable in the tuple for (a) storing the visited state, and (b) when adding/removing from the queue.

Example: Navigating a 2D grid with an option of eliminating at-most `k` obstacles, would require us to define our state as `state = (x, y, k)`  for both BFS queue and visited dictionary. [[Leetcode #1293]](https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/description/)



------



# Depth-First Search (DFS)



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

 



 

