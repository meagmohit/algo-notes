---
layout: default
title: Tricks
parent: Algorithms
nav_order: 15
---

## [Math] Check if a number is perfect square
We add 0.5 to avoid the floating point values for very large numbers [[Ref]](https://djangocentral.com/python-program-to-check-if-a-number-is-perfect-square/)
```python
def check_square (num ):
root = sqrt(num)
int(root + 0.5) ∗∗ 2 == num
```



## [Graph] Word Ladder Graph

Problem Statement: How to make edges for a Graph, in a list of words, where only one character is different? i.e., to add edges between the nodes (words), where only a single character is different.
- For each word, add it to the dictionary with keys having `_` at every character location. Now, for each dictionary key, connect all values as edges in the graph.



