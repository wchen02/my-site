---
layout: post
title: 104. Maximum Depth of Binary Tree
tags: [Python, LeetCode, Easy, Depth-first Search, Tree]
author: wchen02
excerpt_separator: <!--more-->
---
Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

**Note**: A leaf is a node with no children.
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
> **Output**: 3

## Solution

```python
class TreeNode:
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None

class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        return max(1 + self.maxDepth(root.left), 1 + self.maxDepth(root.right))
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

answer = test.maxDepth(None)
assert answer == 0
node1.right = node2
node2.left = node3
answer = test.maxDepth(node1)
assert answer == 3

node1.left = node2
node1.right = node3
node2.left = node4
node2.right = node5
node5.left = node8
node3.left = node6
node3.right = node7
node6.right = node9
answer = test.maxDepth(node1)
assert answer == 4
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(N)

**Time Complexity**: O(N)
