---
layout: default
title: Graphs
nav_order: 2
---

# Union-Find Disjoin Sets
Disjoint Sets are used to address the connectivity in the network. How to quickly check whether two vertices are connected or not (in a graph, not via direct edge). Two Important functions are:
- **Find:** finds the root node of a given vertex. Root node is difference from parent node.
- **Union:** Joins two vertices by making their root node same.

There are four different kinds of implementations. 
1. **Quick Find:** Store the `root` indexes in root array such that the `find` operation is O(1)
2. **Quick Union:** Store the immediate parent index in `root` array such that `union` operation is O(1)
3. **Union by Rank:** `rank` refers to the height of each vertex. When we `union`, we choose the root node of the vertex with the larger rank, i.e. merge the shorter tree under the taller tree.
4. **Union by Rank with Path Compress Optimization:** To find the root node we’re traversing the parents node sequentially, until we reach the root node. These operations are repeated in the Union by Rank method, and hence path compression method removes the redundancy by assigning the root in find function. 

### Complexity Analysis
| Algorithm    | Constructor       | Find   | Union  | Connected | 
|:-------------|:------------------|:-------|
| ok           | good swedish fish | nice   |
| out of stock | good and plenty   | nice   |
| ok           | good `oreos`      | hmm    |
| ok           | good `zoute` drop | yumm   |
  
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

```python
# Implementing Quick Union
class UnionFind:
	def __init__(self, n):
		self.root = [i for i in range(n)]

	def find(self, x):
		while self.root[x]!=x:
			x = self.root[x]
		return x

	def union(self, x, y):
		rootX = self.find(x)
		rootY = self.find(y)
		if rootX!=rootY:
			self.root[rootY] = rootX

	def connected(self, x, y):
		return self.find[x] == self.find[y]
```

```python
# Implementing Union by Rank
class UnionFind:
	def __init__(self, n):
		self.root = [i for i in range(n)]
		self.rank = [1]*n

	def find(self, x):
		while self.root[x]!=x:
			x = self.root[x]
		return x

	def union(self, x, y):
		rootX = self.find(x)
		rootY = self.find(y)
		if rootX!=rootY:
			if self.rank[x] > self.rank[y]:
				self.root[rootY] = rootX
			elif self.rank[y] > self.rank[x]:
				self.root[rootX] = rootY
			else:
				self.root[rootY] = rootX
				self.rank[rootX] += 1

	def connected(self, x, y):
		return self.root[x] == self.find[y]
```

```python
# Implementing Union by Rank with Path Compress Optimization
class UnionFind:
	def __init__(self, n):
		self.root = [i for i in range(n)]
		self.rank = [1]*n

	def find(self, x):
		if x==self.root[x]:
			return x
		self.root[x] = self.find(self.root[x])
		return self.root[x]

	def union(self, x, y):
		rootX = self.find(x)
		rootY = self.find(y)
		if rootX!=rootY:
			if self.rank[rootX] > self.rank[rootY]:
				self.root[rootY] = rootX
			elif self.rank[rootY] > self.rank[rootX]:
				self.root[rootX] = rootY
			else:
				self.root[rootY] = rootX
				self.rank[rootX] += 1

	def connected(self, x, y):
		return self.find(x) == self.find(y)
```
