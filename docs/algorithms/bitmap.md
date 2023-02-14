---
layout: default
title: Bit Manipulations
parent: Algorithms
nav_order: 6
---

# Bit Manipulations
{: .no_toc}


1. TOC
{:toc}

## Mathematical Operations

Consider the `bitmask` is already there, and we need to modify it as per

- Divide by 2 (integer value): `bitmask >> 1`
- Multiply by 2: `bitmask << 1`
- `bitmask - 1`: It will have all the same bits as `bitmask` except for the rightmost `1` in bitmask and all the bits of the right of rightmost `1`. In other words, the binary representation of `bitmask −1` can be obtained by simply flipping all the bits to the right of rightmost `1` in `bitmask` (including the flipping of rightmost `1` as well). E.g. for `bitmask = 20` (i.e., `10100`), we get `bitmask − 1 = 19` (i.e., `10011`)
-  Two Compliment (or `-bitmask`): `-bitmask` is two-complement of `bitmask` OR (1-complement of `bitmask`)-1
-  `bitmask & -bitmask`: Extracts the rightmost 1-bit [[Leetcode #260]](https://leetcode.com/problems/single-number-iii/) 
-  Check power of 2 by `x & (x-1)` [[Leetcode #231]](https://www.hackerearth.com/practice/notes/bit-manipulation/) 
-  Addition (x+y): XOR can be used for adding without carry, and `x&y<<1` can be used for carry. [[Leetcode #67]](https://leetcode.com/problems/add-binary/) 
```python
def add(x,y):
	while y:
	x, y = x ^ y, (x & y) << 1
	return bin(x )[2:]
```

## Counting 1s (Brian Kernighan Algorithm)
Count the total number of ones in the binary representation of a number. [[Leetcode #191]](https://leetcode.com/problems/number-of-1-bits/)

**Solution:** Set the rightmost 1s to zero. [57] O(K) where K is total number of ones

```python
def count1s (num ):
	out = 0
	while num >0: 
		out , num = out +1, num & (num−1)
```



## Counting Number of Occurrences

**Counting odd occurrences:** Since $x \oplus x \rightarrow 0$, XOR operation can be used to count the odd occurrences of  any given number.

**Counting exactly 1 and 2 occurrences**:

```python
seen_once = ~ seen_twice & ( seen_once ^x)
seen_twice = ~ seen_once & ( seen_twice ^x)
```

[[Leetcode #74]](https://leetcode.com/problems/single-number-ii) [[Leetcode #75]](https://leetcode.com/problems/single-number-iii)

## Generate all possible subsets
Each element in a set can be represented with a bit. 
```python
def possibleSubsets(A):
	N = len(A)
	for i in range(2**N):
		for j in range(N):
			if (i & (1<<j))==1: print(A[j])
		print(" ")
```



## References

1. [[Bit manipulation by Hackerrank]](https://www.hackerearth.com/practice/notes/bit-manipulation/)

