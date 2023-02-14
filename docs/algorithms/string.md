---
layout: default
title: String Algorithms
parent: Algorithms
nav_order: 12


---

# String Algorithms
{: .no_toc}


1. TOC
{:toc}


{: .warning}

SECTION INCOMPLETE: Review Content


## Repeated Sequences
The generic problem is to find the `L` length repeated sequences in a given string. [[Leetcode #187]](https://leetcode.com/problems/repeated-dna-sequences/)

### Rabin-Karp Algorithm
If there are `a` unique characters in the string, convert the sub-string of length `L` to a `a-`decimal number (i.e., base `a`). Use hash set to find the repetitions.  **Time Complexity:** O(N)

### Bit Manipulation
Instead of converting it to a `a-`decimal number convert to a bitmask, and operate accordingly. 

{: .note}
**Comparison optimization in sliding window approaches:** Consider a simpler problem of finding a permutation [[Leetcode #567]](https://leetcode.com/problems/permutation-in-string/) or anagram [[Leetcode #438]](https://leetcode.com/problems/find-all-anagrams-in-a-string/) with a 26-sized array to count the frequency of the characters. To reduce the computational complexity (i.e. comparing the 26-element arrays at every step of sliding window), keep a variable `count` and update accordingly to count the number of mismatched letters. For detailed solution, refer to [[Leetcode #567]](https://leetcode.com/problems/permutation-in-string/) 


## Manacher Algorithm for Longest Palindromic Substring
Given a string, find the longest substring which is palindrome. **Time Complexity:** O(N) [[Ref1]](https://www.geeksforgeeks.org/manachers-algorithm-linear-time-longest-palindromic-substring-part-1/) [[Ref2]](https://www.hackerearth.com/practice/algorithms/string-algorithm/manachars-algorithm/tutorial/) [[Ref3]](https://www.youtube.com/watch?v=nbTSfrEfo6M&ab_channel=IDeserve) [[Leetcode #647]](https://leetcode.com/problems/palindromic-substrings/)

**Basic Insights:**
1. For any `idx` in between `(center, right)` interval, the length of palindromic substring is atleast the length calculated for the mirror index (around center, which is `center - (idx-center)`)
2. We expand only beyond that since that much length is already known
3. If the right boundary expands, we update the `center` and `right`

```python
def manacher(s):
    s = "$#"+"#".join(s)+"#@"
    p, center, right = [0]*len(s), 0, 0
    for idx in range(1, n-1):
        mirror = 2*c-idx
        if idx<r: p[idx] = min(r-idx, p[mirror])
        while s[idx+(p[idx]+1)]==s[(idx-(p[idx]+1))]: p[idx]+=1
        if p[idx]+idx>r: c, r = idx, idx+p[idx]
    return p
```

## KMP Algorithm for Pattern Matching
Given a `string` and a `pattern`, find all occurrences of `pattern`. 

### Building Prefix Array
Given the `pattern`, find the longest proper prefix (a proper prefix is prefix with whole string **not** allowed) which is also a suffix. Return an array `lps` such that `lps[i]` represents the longest proper prefix of `pattern[0..i]` (`i` included). A naive algorithm takes $O(n^3)$ time. Note the following insight: $lps[i+1] \leq lps[i]$. **Time complexity**: O(len(pattern))
1. Iteration `i` from `1` to `n-1`, with `lps[0]=0`
2. Denote `j` as the best prefix length, and initialize with `lps[i-1]`. If `pattern[i] == pattern[j]` then `lps[i]=j+1` otherwise keep setting `j` to `lps[j-1]` and repeat. If `j==0`, we set `lps[i]=0` and move to the next `i`. [[Ref1]](https://cp-algorithms.com/string/prefix-function.html) [[Ref2]](https://www.youtube.com/watch?v=KG44VoDtsAA&ab_channel=TusharRoy-CodingMadeSimple)


```python
def KMP_prefixArray(pattern):
    lps = [0]*len(pattern)
    for i in range(1,len(pattern)):
        j = lps[i-1]
        while j>0 and pattern[i]!=pattern[j]: j = lps[j-1]
        if pattern[i]==pattern[j]: lps[i]=j+1
        else: lps[i]=0 #Means $j$ was 0
```



### KMP Algorithm

Given the longest proper prefix array (`lps`), we do not match all characters multiple times to save time complexity. **Time complexity:** O(m+n) [[Ref1]](https://www.geeksforgeeks.org/kmp-algorithm-for-pattern-searching/) [[Ref2]](https://www.youtube.com/watch?v=GTJr8OvyEVQ&ab_channel=TusharRoy-CodingMadeSimple) [[Leetcode #214]](https://leetcode.com/problems/shortest-palindrome/)

- `i,j` denotes the indexes in `string` and `pattern` respectively to compare. 
- If there is a match `s[i]==s[j]`, we increment both pointers
- If there is a mismatch, we know that 
  - `pattern[0..j-1]` matches with `string[i-j....i-1]`
  - `lps[j-1]` is count of characters `pattern[0..j-1]` that are both proper prefix and suffix, hence, we do not need to match `lps[j-1]` characters with `string[i-j....i-1]`.

```python
def KMP(string, pattern):
    m,n, lps = len(pattern), len(string), KMP_prefixArray(pattern)
    i,j,out=0,0,[]
    while (i<n):
        if string[i]==pattern[j]: i, j = i+1, j+1
        if j==m: out.append(i-j)
        else:
            if j==0: i=i+1
            else: j = lps[j-1]
```

