---
layout: default
title: Binary Search Trees
parent: Trees
nav_order: 3
---



# Binary Search Trees (BST)



## Implentation of BST

**Implementation:** Using `TreeNode` class and `BinarySearchTree` class [^bst_implementation]

- `BinarySearchTree` class
  - `def put(self, key, val)` Insert key in BST **O(n)**
  - `def get(self, key)` Get key in BST **O(n)**
  - `def delete(self, key)` Delete key in BST **O(n)**
- `TreeNode` class
  - `def findSuccessor(self)` : find the successor node
  - `def findMin(self)` : find the minimum node in the subtree
  - `def spliceOut(self)` : remove the node







[^bst_implementation]: [PythonDS BST](https://runestone.academy/ns/books/published/pythonds/Trees/BinarySearchTrees.html)