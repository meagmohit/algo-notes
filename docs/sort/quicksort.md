---
layout: default
title: QuickSort
parent: Sorting
nav_order: 1


---

# QuickSort



## Partition Algorithm (For QuickSelect and QuickSort)
**** Given an array and pivot_index, moves smaller element to the left and bigger elements to the right. Return the reshifted pivot_index

**Time Complexity:** O(n); **Space Complexity:** O(1)
```python
def partition(arr, pivot_idx, start, end):
	pivot_val = arr[pivot_idx] 
	arr[pivot_idx], arr[end] = arr[end], arr[pivot_idx] # move pivot to end
	store_idx = start  # move all smaller elements to the left, every element left of store_idx is smaller than pivot
	for idx in range(start, end):
		if arr[idx] <= pivot_val:
			arr[store_idx], arr[idx] = arr[idx], arr[store_idx]
			store_idx += 1
	arr[store_idx], arr[end] = arr[end], arr[store_idx]
	return store_idx
```