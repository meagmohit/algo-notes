---
layout: default
title: Trees Basics
parent: Trees
nav_order: 1
---



# Trees

**Complete Binary Tree:** Each level has all of its nodes. For the last level, the nodes are filled left to right.



## Tree ADT

### Representation 1: List of List

```
[ root, [left subtree], [rightsubtree]]
```
### Representation 2: Nodes and References

```python
class BinaryTree:
	def __init__(self, root):
		self.root = root
		self.left = None
		self.right = None
```



## Tree Traversal

1. **Pre-order:** In a preorder traversal, we visit the root node first, then recursively do a preorder traversal of the left subtree, followed by a recursive preorder traversal of the right subtree.
2. **In-order:** In an inorder traversal, we recursively do an inorder traversal on the left subtree, visit the root node, and finally do a recursive inorder traversal of the right subtree.
3. **Post-order:** In a postorder traversal, we recursively do a postorder traversal of the left subtree and the right subtree followed by a visit to the root node.



{: .note }

>  Inorder traversal is not a unique identifier of BST. At the same time, both preorder and postorder traversal are unique identifiers of BST. [[Ref]](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/solutions/422736/official-solution/ )
>
> - `inorder = sorted(preorder) = sorted(postorder)`
> - For BT, a tree can be made via inorder+preorder or inorder+postorder
