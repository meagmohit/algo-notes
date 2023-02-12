---
layout: default
title: Tricks
parent: Algorithms
nav_order: 13
---

## [Graph] Word Ladder Graph

Problem Statement: How to make edges for a Graph, in a list of words, where only one character is different? i.e., to add edges between the nodes (words), where only a single character is different.
- For each word, add it to the dictionary with keys having `_` at every character location. Now, for each dictionary key, connect all values as edges in the graph.

Example: Given a list `wordList`, return a graph where the words which  differs by a single letter are connected via direct edges [[LC #127: Word Ladder]](https://leetcode.com/problems/word-ladder/description/)

```python
d = defaultdict(list)
for word in wordList:
	for idx in range(len(word)):
	key = word[:idx]+'_'+word[idx+1:]
	d[key].append(word)
g = defaultdict(list)
for key in d.keys():
	total_items = len(d[key])
	for idx in range(total_items):
		word1 = d[key][idx]
		for jdx in range(idx+1, total_items):
		word2 = d[key][jdx]
		g[word1].append(word2)
		g[word2].append(word1)
```



## [Misc] Floyd's Cycle Finding Algorithm

In Linked List, a cycle can be detected by using two pointers, one fast (2x speed) and other slow. If the pointers meet, there is a cycle otherwise not. 

**How to detect the beginning point of cycle?**

Let us consider the two pointers met at node `h`. There are `F` nodes out of the cycle and `(a + b)` nodes inside the cycle. Since, the two pointers met at `h`,


$$
\begin{aligned}
    2*(F+a) &= F + a + b + a,    \; \; mod(a+b) \\
    F &= b,  \; \;  \; \; mod(a+b)
\end{aligned}
$$

1. Set `ptr_1` to the list head, and `ptr_2` to the intersection node.
2. Traverse both pointers one point at a time, the meeting point is the cycle entrance.

![](../../../assets/images/floyd.png)

**Question:** [[Leetcode #142]](https://leetcode.com/problems/linked-list-cycle-ii/description/)

{: .note} 

The next function of linked list can be emulated in arrays using `nums[nums[i]]`. In an `n + 1` element array with elements ranging from `1`to `n`, if there is an element in the array repeated multiple times, it can be detected using the same idea. [[Leetcode #287]](https://leetcode.com/problems/find-the-duplicate-number/)

## [Misc] Exactly K to Atmost(K)
For some problems, it is better to convert exactly K solution to a difference of atmost(K) - atmost(K-1).  For example, consider problem [78], finding the atleast K is easy.
[[Leetcode #992]](https://leetcode.com/problems/subarrays-with-k-different-integers/) 

{: .warning}
To-DO

## [Misc] Finding Top-K

{: .warning}

To-DO

