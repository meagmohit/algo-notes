---
layout: default
title: Dynamic Programming
parent: Algorithms
nav_order: 4
---

# Dynamic Programming
{: .no_toc}


1. TOC
{:toc}

{: .warning}

To-DO: Review the content


## DP for Longest Common Subsequence
Given two sequences $X, Y$, find the length of longest subsequence present in both of them. A subsequence is a sequence that appears in the same relative order, but not necessarily contiguous [[Leetcode #1143]](https://leetcode.com/problems/longest-common-subsequence/)

```python
if X[i-1]==Y[j-1]:
    dp[i][j] = 1 + dp[i-1][j-1]
else:
    dp[i][j] = max(dp[i-1][j], dp[i][j-1])
```
**Other Problems:** [[Leetcode #1035]](https://leetcode.com/problems/uncrossed-lines/) [[Leetcode #1458]](https://leetcode.com/problems/max-dot-product-of-two-subsequences/)

## DP for 0/1 KnapSack
Given $weights (wt)$ and $values (val)$ for $n$ items, put these items in a knapsack of capacity $W$ to get the maximum total value in the knapsack. You can either pick a weight or choose to not pick it (i.e., 0/1 relationship). [[Ref]](https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/) [[Leetcode #416]](https://leetcode.com/problems/partition-equal-subset-sum/)

```ptyhon
dp = [[0]*(W+1) for i in range(n+1)]
for i in range(n+1):
    for w in range(W+1):
        if i==0 or w==0: dp[i][w]=0
        dp[i][w] = dp[i-1][w]
        if wt[i-1]<=w:
            dp[i][w] = max(val[i-1] + dp[i-1][w - wt[i-1], dp[i][w])
```

{: .note}

Trick for Space Complexity — To reduce space complexity from O(N W ) to O(W ), use one dimensional
dp array, and loop for W in reverse order.


## DP with Bitmasking
There are $N$ persons and $N$ tasks, each task is to be alloted to a single person. We are also given a matrix $cost$ of size $N\times N$, where $cost[i][j]$ denotes, how much person $i$ is going to charge for task $j$. Now we need to assign each task to a person in such a way that the total cost is minimum. Note that each task is to be alloted to a single person, and each person will be alloted only one task. [[Ref]](https://www.hackerearth.com/practice/algorithms/dynamic-programming/bit-masking/tutorial/)

```python
def assign(N, cost):
  size = 1<<n
  dp = [float("inf")]*(size)
  dp[0] = 0
  for mask in range(size):
    x = count_set_bits(mask)
    for j in range(N):
      if jth bit is not set in mask:
      	dp[mask|(1<<j)] = min(dp[mask|(1<<j), dp[mask]+cost[x][j]
```
[[Hamiltonian Paths w/ DP Bitmasking]](https://www.hackerearth.com/practice/algorithms/graphs/hamiltonian-path/tutorial/)



