---
layout: default
title: Randomized Algorithms
parent: Algorithms
nav_order: 8
---

# Randomized Algorithms

## Reservoir Sampling

Choose `k` elements from a stream (of `n` elements), in a uniform random manner without replacement.

**Proof**:

- Goal: Probability of any `ith` element to be selected in result, should be `k/n`
- Case 1: $k < i \leq n$
  - Probability of `nth` element to be selected is `k/n`    [fix this proof while writing on latex]
  - Probability of `(n-1)th` element to be selected: one of the `kth` indexes was chosen for `(n-1)th`, and the same index was not chosen for the `nth`: $\frac{k}{n-1}. \frac{n-1}{n}$
  - Similarly, for `(n-2)th` etc.

- Case 2: $i \leq k$
  - Probability that item is not picked for `k+1`, `k+2`, ... , `n`, i.e., $\frac{k}{k+1}.\frac{k+1}{k+2} \cdots \frac{n-1}{n}$

**Time Complexity:** $O(n)$;  **Space Complexity:** $O(k)$

```python
def reservoir_sampling(stream, k):
	res = [stream[i] for i in range(k)]
	for i in range(k, n):
		# returns random int inclusive of given range
		rand_idx = random.randint(0,i)
		if rand_idx < k: res[rand_idx] = stream[i]
	return res
```



## Fisher-Yatts Shuffle Algorithm

Randomly shuffle an array (of `n` elements), in a uniform random manner without replacement.

**Proof:**

- Goal: Probability of any `ith` element to be at any index should be `1/n`
- Probability of `ith` element to be in the last position is `1/n`
- Probability of `ith` element to be in the second last position is:
  - Case 1 for last element $i==n-1$: Item was replaced in 1st iteration, and same index was chosen for 2nd: $\frac{n-1}{n}. \frac{1}{n-1}$
  - Case 2 for other than last element $i<n-1$: Item was not chosen in the 1st iteration (for nth index) and chosen for 2nd: $\frac{n-1}{n}. \frac{1}{n-1}$
- Can be generalized for other elements

**Time Complexity:** $O(n)$  **Space Complexity:** $O(1)$

```python
def shuffle(arr):
	n = len(arr)
	for idx in range(n-1, 0, -1):
		rand_idx = random.randint(0, idx)
		arr[idx], arr[rand_idx] = arr[rand_idx], arr[idx]
	return arr
```



# References

- [Reservoir Sampling](https://www.geeksforgeeks.org/reservoir-sampling/ )
- [Fisher–Yates Shuffle Algorithm](https://www.geeksforgeeks.org/shuffle-a-given-array-using-fisher-yates-shuffle-algorithm/)