---
layout: default
title: Sorting Algorithms
parent: Algorithms
nav_order: 5


---

{: .warning}
SECTION INCOMPLETE: Write all sorting algorithms w/ their time complexities

# QuickSort



# QuickSelect Algorithm

FInds $K^{th}$ smallest element in an unordered list.

**Solution Approach:** For recursive solution in quickselect, if index of partitioned element is more than k, then we recur for left part. If index is same as k, we have found the top-K and we return. If index is less than k, then we recur for right part.

```python
def quickselect(left, right, topK):
    if left==right: return
    pivot_idx = partition(left, right, random.randint(left, right))
    if pivot_idx == topK: return
    elif pivot_idx < topK: return quickselect(pivot_idx+1, right, topK)
    else: return quickselect(left, pivot_idx-1, topK)
```

**Time Complexity:** $O(N)$ in the average case (randomly chosen pivot, such that problem is divided in half in each iteration),  and $O(N^2)$ in the worst case (e.g. pivot is always right, when the problem size reduces to only 1 at each step).

## Partition Algorithm (For QuickSelect and QuickSort)

1. Move pivot at the end of the array using swap.
2. Set the pointer at the beginning of the array `store_index = start`.
3. Iterate over the array and move all less frequent elements to the left `swap(store_idx, i)`. Move `store_idx` one step to the right after each swap.
4. Move the pivot to its final place, and return this index.

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





## MergeSort vs. QuickSort
- Worst case complexity of Quicksort is $O(n^2)$ while mergesort is O(nlogn).
- Quicksort (efficient and faster) works well for shorter size arrays, while Mergesort works better for higher-sized arrays.
- Mergesort requires additional space while quicksort performs in-place operations.
- Mergesort is stable, and quicksort can be made stable with some changes in the code.
- Mergesort is preferred for linked lists, while quicksort is preferred for arrays


# References

- [Runstone Academy PythonDS Book Chapter 6.6-6.12: Sorting](https://runestone.academy/ns/books/published/pythonds/SortSearch/toctree.html)
- [QuickSelect Problems](https://leetcode.com/tag/quickselect)