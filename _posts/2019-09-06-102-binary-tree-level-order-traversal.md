---
layout: post
title: 102. Binary Tree Level Order Traversal
tags: [Python, LeetCode, Medium, Bread-first Search, Tree]
author: wchen02
excerpt_separator: <!--more-->
---

Given a binary tree, return the *level order* traversal of its nodes' values. (ie, from left to right, level by level).
<!--more-->

**Example**:
> **Input**:
> `[3, 9, 20, null, null, 15, 7]`,
> <pre>
>     3
>    / \
>   9  20
>     /  \
>    15   7
> </pre>
>
> **Output**:
> <pre>
> [
>   [3],
>   [9,20],
>   [15,7]
> ]
> </pre>

## Solution

```python
from typing import List
from collections import deque

class TreeNode:
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None

class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []

        result = []
        q = deque([root])

        while q:
            levelNodes = []
            for _ in range(len(q)):
                node = q.popleft()
                levelNodes.append(node.val)

                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)

            result.append(levelNodes)
        return result
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

answer = test.levelOrder(None)
assert answer == []
node1.right = node2
node2.left = node3
answer = test.levelOrder(node1)
assert answer == [[1], [2], [3]]

node1.left = node2
node1.right = node3
node2.left = node4
node2.right = node5
node5.left = node8
node3.left = node6
node3.right = node7
node6.right = node9
answer = test.levelOrder(node1)
assert answer == [[1], [2, 3], [4, 5, 6, 7], [8, 9]]
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(N)

**Time Complexity**: O(N)
