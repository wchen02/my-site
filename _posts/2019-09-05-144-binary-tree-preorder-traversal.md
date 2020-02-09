---
layout: post
title: 144. Binary Tree Preorder Traversal
tags: [Python, LeetCode, Medium, Stack, Tree]
author: wchen02
excerpt_separator: <!--more-->
---

Given a binary tree, return the *preorder* traversal of its nodes' values.
<!--more-->

**Example**:
> **Input**:
> [1, null, 2, 3]
> <pre>
> 1
>  \
>   2
>  /
> 3
> </pre>
>
> **Output**:
> [1, 2, 3]

**Follow up**: Recursive solution is trivial, could you do it iteratively?

## Solution

```python
from typing import List

class TreeNode:
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None

class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        list = []
        stack = []

        while root or stack:
            while root:
                list.append(root.val)
                stack.append(root)
                root = root.left
            root = stack.pop()
            root = root.right

        return list
```

## Test Cases

```python
test = Solution()
node1 = TreeNode(1)
node2 = TreeNode(2)
node3 = TreeNode(3)
node4 = TreeNode(4)
node5 = TreeNode(5)
node6 = TreeNode(6)
node7 = TreeNode(7)
node8 = TreeNode(8)
node9 = TreeNode(9)

answer = test.preorderTraversal(None)
assert answer == []
node1.right = node2
node2.left = node3
answer = test.preorderTraversal(node1)
assert answer == [1,2,3]

node1.left = node2
node1.right = node3
node2.left = node4
node2.right = node5
node5.left = node8
node3.left = node6
node3.right = node7
node6.right = node9
answer = test.preorderTraversal(node1)
assert answer == [1,2,4,5,8,3,6,9,7]
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(N)

**Time Complexity**: O(N)
