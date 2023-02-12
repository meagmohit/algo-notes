---
layout: default
title: Heaps
parent: Data Structures
nav_order: 3
---

# Heaps

## Heaps ADT

A list can represent the heap, with keeping 0th index as dummy node. If we start the indexing from 1,

- For parent index `i`, the left child is `2*i` and right child is `2*i +1`
- For any child index `i`, the parent node is `i//2`
- We keep the heap balanced by creating a complete Binary Tree
- Python library: `import heapq`

## Heap Functions

- **Insert Element:**  `heapq.heappush(h, item)` Append the item in the last and percolate up (i.e. keep swapping with parent node until the heap property satisfies)
- **Delete Minimum Element:** `heapq.heappop(h)` Swap the minimum element with the last item of the heap, and remove the last item. Percolate down from the first element, until the heap property satisfies
- **Heapify:** `heapq.heapify(items)` Keep Percolating Down from the middle element of the heap, until the first element

### Complexity Analysis

| Operation      | Time Complexity |
| -------------- | --------------- |
| Insert         | `O(log(n))`     |
| Delete Minimum | `O(log(n))`     |
| Find Minimum   | `O(1)`          |
| Heapify a list | `O(N)`          |

### Implementation


```python
class minHeap:
	def __init__(self):
		self.items = [0]
		self.size = 0

	def insert(self, key):
		self.items.append(key)
		self.size += 1
		self.percUp(self.size)
	
	def percUp(self, i):
		while i//2>0 and self.items[i//2]<self.items[i]:
			self.items[i//2], self.items[i] = self.items[i], self.items[i//2] 
			i = i//2
	
	def delMin(self):
		last_item = self.items.pop()
		retVal = self.items[1]
		self.items[1] = last_item
		self.size -= 1
		self.percDown(1)
		return retVal
	
	def percDown(self, i):
		mc = self.minChild(i) 
		while mc and self.items[mc] < self.items[i]:
			self.items[i], self.items[mc] = self.items[mc], self.items[i]
			i = mc
			mc = self.minChild(i)
	
	def minChild(self, i):
		if 2*i > self.size: return None
		if 2*i+1 <= self.size and self.items[2*i+1] < self.items[2*i]: return 2*i+1
		return 2*i
	
	def heapify(self, items)
		self.items[1:] = items[:]
		self.size = len(items)
		for i in range(self.size//2,0,-1):
			self.percDown(i)
```



# References

- [Runstone Academy PythonDS Book Chapter 7.8-7.10: Priority Queues](https://runestone.academy/ns/books/published/pythonds/Trees/PriorityQueueswithBinaryHeaps.html)
- 
