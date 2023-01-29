---
layout: default
title: Graphs
nav_order: 2
---

# Union-Find Disjoin Sets
Disjoint Sets are used to address the connectivity in the network. How to quickly check whether two vertices are connected or not (in a graph, not via direct edge)

Two Important functions are:
- Find: finds the root node of a given vertex. Root node is difference from parent node.
- Union: Joins two vertices by making their root node same.

There are four different kinds of implementations. 
1. Implementing Quick Find: Store the <root> indexes in root array such that the <find> operation is O(1)
2. Implementing Quick Union
3. Implementing Union by Rank
4. Implementing Union by Rank with Path Compress Optimization
  
```python
# Implementing Quick Find
class UnionFind:
	def __init__(self, n):
		self.root = [i for i in range(n)]

	def find(self, x):
		return self.root[x]

	def union(self, x, y):
		rootX = self.find(x)
		rootY = self.find(y)
		if rootX!=rootY:
			for i in range(len(self.root)):
				if self.root[i]==rootY: 
					self.root[i] = rootX

	def connected(self, x, y):
		return self.root[x] == self.root[y]
```
