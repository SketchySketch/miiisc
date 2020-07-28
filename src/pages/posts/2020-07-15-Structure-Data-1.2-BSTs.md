---
title: Structure Data 1.2 BSTs
date: "2020-07-12"
excerpt: >-
  Binary Search Tree or BST is an effective data structure. In this article I will introduce it and bring you the code of creating, adding, removing, searching and altering BSTs.
layout: post
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

Notice that the mid-order traversal of a BST returns a increasing array. **This property is important!**

# Adding nodes

Let us go into the code straight.

```python
# Defining

import BinaryTree as BTree

class BinarySearchTree(BTree.BinaryTree):
  def __init__(self,root=0,count=0,height=0):
    BTree.BinaryTree.__init__(self,root,count,height)
```

```python
  def insertNode(self,treenode):
    # Check for None

    if treenode == 0:
      return
    if self.root == 0:
      self.root = treenode
      return
    self.count += 1
      currentNode = self.root
      while currentNode :
            if currentNode.data<treenode.data:
                if currentNode.right==0:
                    currentNode.right = treenode
                    return
                else:
                    currentNode = currentNode.right
            elif currentNode.data>treenode.data:
                if currentNode.left==0:
                    currentNode.left = treenode
                    return
                else:
                    currentNode = currentNode.left

    def delNode(self,currentnode,data):
        if not currentnode.left and not currentnode.right:
            currentnode.data = None
            return 'leaf'
        if currentnode.data is data:
            if currentnode.left and currentnode.right:
                rightnode = currentnode.right
                rightparent = rightnode
                while rightnode.left:
                    rightparent = rightnode
                    rightnode = rightnode.left
                currentnode.data = rightnode.data
                if self.delNode(rightnode,rightnode.data) is 'leaf':
                    rightparent.left = None
                return 'node'
            else:
                direction = 0 if currentnode.left else 1
                node = currentnode[direction]
                currentnode.data = node.data
                if self.delNode(node,node.data) is 'leaf':
                    currentnode[direction] = None
                return 'node'
        else:
            parent = currentnode
            direction = 0 if currentnode.data > data else 1
            currentnode = parent[direction]
            if self.delNode(currentnode,data) is 'leaf':
                parent[direction] = None
```

References:

1. [CSDN Blog](https://blog.csdn.net/l153097889/article/details/46839823)
