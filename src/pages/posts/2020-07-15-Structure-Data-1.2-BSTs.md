---
title: Structure Data 1.2 BSTs
excerpt: >-
  Binary Search Tree or BST is an effective data structure. In this article I will introduce it and bring you the code of creating, adding, removing, searching and altering BSTs.
date: "2020-07-30"
template: post
---

# Beyond Traversal

In the previous section we talked about binary trees and the three traversal methods. All the methods works well. But!!! We don't just need to traverse -- we also need to return an array, and we hope the array has some _properties_ -- like it's _sorted_. This is a very important beginning.

## BSTs

BSTs is the short for Binary Search Trees. By using BST we can store and get data very easily.

We store data by the rule described below:

```
For a node R and a number N != R, if N < R then append N to R.left; else append N to R.right.
```

## A Secret of Mid-Order Traversal and BST

```
    5
   / \
  2   6
 / \   \
1   4   8
   /   / \
  3   7   9 A BST.

1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 9 Mid-order traversal
```

Notice that the mid-order traversal of a BST returns an increasing array. **This property is important!**

```
Proof for the curious

Why the mid-order traversal of a BST is an increasing array? Because in mid-order traversal method we first explore the left tree, which is always the smallest ones; then the root, always the median;then the right, always the largest ones. So after 1 round of recursion the array generated is[ALL-THE-SMALL-ONES, MEDIAN, ALL-THE-LARGE-ONES].
After many rounds of recursion, all the small ones will be throws to the left of the current median, and the large ones to the right.
```

# Performing the BST

## Adding nodes
Adding a node is as easy as pie. By recursion we compare the number `t` and the current `root` to determine where is the next step.

```python
# For convenience I'll be using Python-like pseudo-code.

def add(node, bst):
    if node < bst.root:
        if bst.IS_LEAF:
            bst.left = node
            return True
        add(node, bst.left)
    elif node > bst.root:
        if bst.IS_LEAF:
            bst.right = node
            return True
        add(node, bst.right)
    else:
        return False
```

