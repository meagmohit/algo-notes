---
layout: default
title: Sliding Window Patterns
parent: Algorithms
nav_order: 9
---

# Sliding Window Patterns

An abstract concept commonly used in array or string problems. A **window** is a range of elements in the array/string which usually defined by the start and end indices. 

**Problems: **Typically the problems are similar to `(*Longest/Shortest/Number of*) (*Substrings/Subarrays*) with (*At most/Exactly*) K elements that fit (*some condition*)`. Few examples are below,

1. Given a string `s`, find the length of the longest substring without repeating characters. [[Leetcode #3]](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)
2. Given a string `s` and an integer `k`, return *the length of the longest* *substring* *of* `s` *that contains at most* `k` *distinct characters*. [[Leetcode #340]](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)
3. Given two strings s and t of lengths m and n respectively, return the minimum window 
substring  of s such that every character in t (including duplicates) is included in the window. [[Leetcode #76]](https://leetcode.com/problems/minimum-window-substring/)


**Solution Approach 1:** The general approach is to keep two pointers `left` and `right`. We keep increasing the right pointer. [[Ref]](https://leetcode.com/tag/two-pointers/discuss/1122776/Summary-of-Sliding-Window-Patterns-for-Subarray-Substring)

- If the element at the right pointer makes the window not valid, we keep moving the left pointer to shrink the window until it becomes valid again.
- Then, we update the global min/max with the result from the valid window.
- To check if it is valid, we need to store the "state" of the window (ex. frequency of letters, number of distinct integers).

```python
for right in range(n):
    update window with element at right pointer
    while (condition not valid):
        remove element at left pointer from window, move left pointer to the right
    update global max
```

For an example, solution of Problem 2 would look like:

```python
def lengthOfLongestSubstringKDistinct(s, k):
	left_ptr, count = 0, defaultdict(int)
	n = len(s)
	n_distinct, res = 0, 0
	for right_ptr in range(n):
		count[s[right_ptr]]+=1
		if count[s[right_ptr]]==1: n_distinct = n_distinct+1
		while (n_distinct > k):
			count[s[left_ptr]]-=1
			if count[s[left_ptr]]==0: n_distinct-=1
			left_ptr += 1
		res = max(res, right_ptr-left_ptr+1)
return res
```

Other (Differently Worded) Sliding Window Problems:
1. [[Leetcode #1004]](https://leetcode.com/problems/max-consecutive-ones-iii/)
2. [[Leetcode #904]](https://leetcode.com/problems/fruit-into-baskets/)
3. [[Leetcode #424]](https://leetcode.com/problems/longest-repeating-character-replacement/)



References

1. [[Summary of Sliding Window Patterns for Subarray / Substring]](https://leetcode.com/tag/two-pointers/discuss/1122776/Summary-of-Sliding-Window-Patterns-for-Subarray-Substring)