---
layout: default
title: Python Refresher
parent: Basics
nav_order: 4

---

# Python Refresher
{: .no_toc }

#### Table of contents
{: .no_toc }

1. TOC
{:toc}

## Python Data Types

- **Built-in atomic data types:** `int`, `float`, and `bool`
- **Built-in collection data types:** `list`, `string`, and `tuple`
  - **List:** Sequentially ordered collection, mutable and heterogeneous  `myList = [1, 3, True, 6.5]`
  - **String:** Sequential collection of characters, immutable `myString = "Mohit"`
  - **Tuple:** Heterogeneous sequences of data, immutable `myTuple = (2, True, 4.96)`
  - **Set:** Unordered collection of zero or more immutable data items, heterogeneous `mySet = {3, "Ca", 4.5, False}` or `myEmptySet = set()`
  - **Dictionary:** Unordered structure with pair of items of key and value `capitals = {'Iowa':'DesMoines','Wisconsin':'Madison'}`

{: .note}
Variable names can start from letter and underscore(_), and are case-sensitive. A reference pointer is created to the data type when an assignment operator is used (e.g., `theSum = 0`)

**Mutability:** The property to get modified. e.g., In the list, an item can be modified using indexing and assignment. However, in the string, the item can not be modified

```python
myName = "Mohit", myTuple = (2, True, 4.96)
myName[0] = 'R' # Not allowed
myTuple[1] = False # Not allowed
```

------

## High-Performance Data Types

### Collections
- **Counter:** Dictionary to count number of occurrences
- **Deque:** Queue w/ both ends, operations: `deque([iterable])`, `append()`, `appendleft()`, `pop()`, `popleft()`. All append and pop operations are O(1)
- **DefaultDict:** Does not raise a key error
- **OrderedDict:** Maintains and remembers the insertion order
```python
import collections
count = collections . Counter (<list >)
deque = collections . deque ()
def_dict = collections . defeaultdict () # attributes: list, int, set
ord_dict = collections . OrderedDict ()
```

### Priority Queues or Binary Heap
- `import heapq`
- `heapq.heapify(iterable)`: Make a new heap [TC: O(n)]
- `heapq.heappush(heap, elem)`: Push the value item onto the heap. [TC: O(logn)]
- `heapq.heappop(heap)`: Pop and return the smallest item from the heap. [TC: O(logn)]
- `heap[-1]`: Peek the smallest element [TC: O(1)]
- In python, it is implemented as List. 
- For maxheap, multiple all elements with `-1`

### Sets
Use sets to convert a list into O(1) lookup (instead of converting it into a dictionary)
```python
set(<list >)
```

------

## Python Functions

### String Tricks

- Joining an iterable with a separator: `separator.join(iterable)`
```python
s = " 123456 "
"_".join(s) #1_2_3_4_5_6
```

- Splitting an string: `string.split(separator, maxsplit)`
```python
s = "12 _34_56_78 "
s. split ("_") #["12" , "34" , "56" , "78"]
```

- String Manipulations: cases
```python
a = " ABcdEF "
a_lower = a. lower () # " abcdef "
a_upper = a. upper () # "ABCDEF"
a_sent = a. capitalize () # "Abcdef"
```
- Check if character is alphanumeric: `s.isalnum(): returns True/False`

### Using map function
`map(func, iter)`: Returns a map object (an iterator) of the results after applying the given function to each item of a given iterable.
- Example: `x = map(str, nums)` returns all numbers in nums array as strings

### Using `sort` and `sorted` functions
- `x = sorted(nums)` returns the sorted array
- Returns the sorted with custom comparator
  - `x = sorted(nums, key=newKey) class newKey(str)   def __lt__(x, y):       return x+y > y+x`
  
```python
<list >. sort(key= lambda x:x[0] , reverse =True) #returns Nothing
sorted (<list >, key= lambda x:x[0] , reverse =True)
```
### Generating Random Numbers
`random.randint(a,b)`: give random integer including a and b

### Custom Comparators
Add custom comparators in python for any operations like sort, etc. In cases like heapq, the best way to add custom comparator is to make it a tuple with the first element being
one that accepts normal python comparator. [[Ref]](https://stackoverflow.com/questions/8875706/heapq-with-custom-compare-predicate)
```python
def compare (item1 , item2):
	if len(item1) > len(item2): return 1
	elif len(item1) < len(item2): return −1
	return 0
words.sort(cmp = compare)
```


## Classes

- Constructors are called using `__init__(self, params)`
- Class object can be converted into string as (used by `print` function) `__str__(self)`
- A list of objects when printed uses function `__repr__(self)`
- Arithmetic operators `__add__(self, other)`
- Equality `__eq__(self, other)`

### Inheritance in Classes

**IS-A relationship**
- In the parent classes, we can define functions which will be implemented in Child classes
- In child class, the constructor needs to call the parent class constructor
    - `parent_class.__**init__**(self, parent_class_params)`
    - `super(child_class, self).__**init__**(parent_class_params)`

## References vs. Copying

**Cloning a list:** `newList = oldList[:]`


## Important Functions
- `range`
- `input(String)` : Prompts a String message to ask user for an input, and returns the String


## Miscellaneous
- Reversing a string: s[::-1]