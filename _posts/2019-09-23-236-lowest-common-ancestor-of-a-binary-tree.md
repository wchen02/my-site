---
layout: post
title: 236. Lowest Common Ancestor of a Binary Tree
tags: [Python, LeetCode, Medium, Tree]
author-id: wchen02
excerpt_separator: <!--more-->
---
Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow **a node to be a descendant of itself**).”
<!--more-->

Given the following binary tree:  root = [3, 5, 1, 6, 2, 0, 8, null, null, 7, 4]

![Binary Tree]({{ "/assets/img/posts/binarytree.png" | relative_url}})

**Example 1**:
> **Input**:
> root = `[3, 5, 1, 6, 2, 0, 8, null, null, 7, 4]`, p = 5, q = 1
>
> **Output**: 3
>
> **Explanation**: The LCA of nodes 5 and 1 is 3.

**Example 2**:
> **Input**:
> root = `[3, 5, 1, 6, 2, 0, 8, null, null, 7, 4]`, p = 5, q = 4
>
> **Output**: 5
>
> **Explanation**: The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.

**Note**:

- All of the nodes' values will be unique.
- p and q are different and both values will exist in the binary tree.

## Solution

```python
from Util.binaryTree import TreeNode
from typing import Dict
from collections import deque

class Solution:
    def lowestCommonAncestor(self, root: TreeNode, p: TreeNode, q: TreeNode) -> TreeNode:
        if q == p:
            return q

        if q == root or p == root:
            return root

        nodeParent = { root.val: root }
        nodeStack = [root]

        while nodeStack:
            walker = nodeStack.pop()
            if walker.left:
                nodeParent[walker.left.val] = walker
                nodeStack.append(walker.left)
            if walker.right:
                nodeParent[walker.right.val] = walker
                nodeStack.append(walker.right)

        ancestorDict = { root.val: root }
        while p != root:
            ancestorDict[p.val] = nodeParent.get(p.val)
            p = nodeParent.get(p.val)

        while not ancestorDict.get(q.val):
            q = nodeParent.get(q.val)

        return q
```

## Test Cases

```python
from Util.binaryTree import TreeNode, Codec
test = Solution()
codec = Codec()

root = codec.deserialize('[3,5,1,6,2,0,8,null,null,7,4]')
p = TreeNode(5)
q = TreeNode(1)
answer = test.lowestCommonAncestor(root, p, q)
assert answer.val == 3

root = codec.deserialize('[3,5,1,6,2,0,8,null,null,7,4]')
p = TreeNode(5)
q = TreeNode(4)
answer = test.lowestCommonAncestor(root, p, q)
assert answer.val == 5

root = codec.deserialize('[3,5,1,6,2,0,8,null,null,7,4]')
p = TreeNode(3)
q = TreeNode(3)
answer = test.lowestCommonAncestor(root, p, q)
assert answer.val == 3

root = codec.deserialize('[3,5,1,6,2,0,8,null,null,7,4]')
p = TreeNode(0)
q = TreeNode(0)
answer = test.lowestCommonAncestor(root, p, q)
assert answer.val == 0
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(N)

**Time Complexity**: O(N)
