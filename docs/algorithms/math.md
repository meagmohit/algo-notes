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



## Computing Power ($x^n$)

For the below codes, consider $n > 0$. [[Leetcode #50]](https://leetcode.com/problems/powx-n/description/)

**Recursive Algorithm:**
Space Complexity: O(logN)

```python
def pow(x,n):
    if n==0: return 1
    if n %2==0: return pow(x,n//2)∗ pow(x,n//2)
    else: return x∗pow(x ,(n−1)//2)∗pow(x ,(n−1)//2)
```

**Iterative Algorithm:** Consider `n` in its binary form, i.e., $b_1 b_2 \cdots, b_{length\_limit}$. Now, $x^n = x^{\sum_i b_i 2^i}$. Keep a variable `current_product` of $x^{2^i}$ and add it to the answer when $b_i$ is 1.  Space complexity is O(1).

```python
def pow(x,n):
    current_product , ans= x, 1
    while n >0:
        if n %2==1: ans = ans∗current_product
        current_product = current_product∗current_product
        n = n//2
```


## Prime Decomposition
Decompose any given number into a series of prime factors
```python
def primeDecompose (num ):
    prime_factors , factor = [], 2
    while num >= factor∗factor :
        if num%factor==0:
        	num=num//factor
	        prime_factors.append(factor)
        else: factor +=1
    prime_factors.append (num)
    return prime_factors
```

## Power Sets
Given a set of unique integer `nums`, return all possible subsets. [[Leetcode #78]](https://leetcode.com/problems/subsets/)

**Algorithm 1:** Cascading Based Approach **TC/SC:** $O(N.2^N)$

```python
def make_power_set (nums ):
    power_set = [[]]
    for num in nums:
    	new_elems = []
    	for item in power_set :
    		new_elems.append(item + [num])
	power_set = power_set + new_elems
    return power_set
```

**Algorithm 2:** Use backtracking/DFS based approach, **TC:** $O(N.2^N)$ **SC:** $O(N)$
```python
def make_power_set(nums):
	n = len(nums)
	power_set = []
	def dfs(k, first =0, curr =[]):
		if len(curr)==k:
			power_set.append (curr [:])
			return
		for i in range(first , n):
			curr.append(nums[i]) # add nums[ i ] into the current combination
			dfs(k, i+1, curr) # use next integers to complete the combination
			curr.pop() # backtrack
			return
	for k in range(n+1):
		dfs(k)
	return power_set
```

**Algorithm 3:** Bit-masking based, generates lexicographic subsets **TC/SC:** $O(N.2^N)$
```python
def make_power_set(nums):
	n = len(nums)
	power_set = []
	for i in range (2∗∗n, 2∗∗(n+1)):
		mask = bin(i)[3:]
		curr = []
		for idx , char in enumerate(mask):
			if char=="1": curr.append(nums[idx])
		power_set.append(curr)
	return power_set
```

## Combinations and Permutations
Combinations: Make `k-`length combinations from `n` elements. The solution approach is similar to DFS/backtracking with power sets, with fixing the length to `k`. **TC:** $O(k.C^N_k)$, **SC:** $O(C^N_k)$.  [[Leetcode #77]](https://leetcode.com/problems/combinations/)
```
def make_combinations(n, k):
    self.out = []
    def dfs(first=0, curr=[]):
        if len(curr)==k:
            self.out.append(curr[:])
        for i in range(first, n):
            curr.append(i)
            dfs(i+1, curr)
            curr.pop()
    dfs()
    return self.out
```

Permutations: The solution approach is similar to DFS/backtracking with power sets with fixed length `n`, however, this time we only swap insetad of skipping over the numbers. **TC:** $O(N.N!)$, **SC:** $O(N!))$ [[Leetcode #46]](https://leetcode.com/problems/permutations/)
```python
def make_permutations(nums):
    n = len(nums)
    self.out = []
    def dfs(first=0):
        if first==n:
            self.out.append(nums[:])
        for i in range(first, n):
            nums[first], nums[i] = nums[i], nums[first]
            dfs(first+1)
            nums[first], nums[i] = nums[i], nums[first]
    dfs()
    return self.out
```