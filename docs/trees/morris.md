---
layout: default
title: Morris Traversal
parent: Trees
nav_order: 5
---

# Morris Traversal [ADVANCED]

To traverse all the nodes in a binary tree without using additional space. We will see below an implementation of the inorder traversal using Morris algorithm. [[Ref]](https://www.geeksforgeeks.org/inorder-tree-traversal-without-recursion-and-without-stack/)

```python
def inorder(root):
    curr = root
    while curr:
        if curr.left is None:
            print curr.val
            curr = curr.right
        else:
            pred = curr.left
            while (pred.right is not None) and (pred.right is not curr):
                pred = pred.right
            if pred.right is None:
                pred.right = curr
                curr = curr.left
            else:
                pred.right = None
                print curr.val
                curr = curr.right
```

