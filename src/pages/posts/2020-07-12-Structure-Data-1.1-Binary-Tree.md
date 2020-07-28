---
title: Structure Data 1.1 Binary Tree
date: "2020-07-12"
excerpt: >-
  Binary tree is a data structure represented as a tree. Binary tree have three traversing ways, and in-order traversal is usually used in Binary Search Trees (BSTs), while post-order traversal is usually used in parsing.
layout: post
---

# Introduction
**A binary tree is made of nodes**, where each node contains *a "left" reference*, *a "right" reference*, and *a data element*. The topmost node in the tree is called the **root**.

Each node (excluding a root) in a binary tree is connected by a directed edge from exactly one other node. This node is called a **parent**. On the other hand, each node can be connected to 2 nodes, called children. Nodes with no children are called **leaves**, or *external nodes*. Nodes which are not leaves are called *internal nodes*. Nodes with the same parent are called *siblings*. [(from cs.cmu.edu, slightly modified)](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Trees/trees.html)

This is a binary tree:
```
      9
     / \
    8   7
   / \   \
  6   5   4
   \     /
    3   2
         \
          1
```

This is not a binary tree:
```
      9
     / \
    8   7
   /|\   \
  6 0 5   4
   \     /
    3   2
         \
          1
```
This isn't, either:
```
      9
     / \
    8   7
   / \   \
  6   5   4
   \     /
    3   2
     \ /
      1
```

We can now define the `BinaryTree` class by its definition.

```python
class BinaryTree:
  def __init__(self, val, left, right):
    self.val = val
    self.left = left
    self.right = right
```
Notice that **val is not null, while left and right can be null.**

## Traversal

### PreOrder Traversal

#### Definition

**PreOrder traversal** method first traverses the root, then the left tree, then the right tree.

For example:

```
     1
    / \
   2   5
  / \   \
 3   4   6 Numbers mean the order.
```

#### Code
The PreOrder traversal can be done easily by recursion.

```python
def preOrder(tree):
  def recursion(tree, startValue): # Start value contains the traversed nodes
    if tree is None:
      startValue.append(tree.val)
      return startValue
     recursion(tree.left, startValue)
     recursion(tree.right, startValue)
  return recursion(tree, [])
```

### InOrder and PostOrder

They are *__very very very similar to PreOrder__*, so I'll only talk about the definitions.

#### InOrder Traversal

First traverses the left tree, then the root, then the right tree. Notice that it is commonly used in BSTs.

#### PostOrder Traversal

First traverses the left tree, then the right tree, then the root.
