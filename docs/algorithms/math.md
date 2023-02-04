---
layout: default
title: Math Algorithms
parent: Algorithms
nav_order: 5
---

# Math Algorithms

## Euclidean Algorithm for GCD
If we keep subtracting the small number from the large number, we end up with GCD
```python
def gcd(a,b):	# 	if a > b: a, b = b, a
	if a==0: return b
	return gcd(b%a, a)
```

