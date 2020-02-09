---
layout: post
title: 101. Symmetric Tree
tags: [Python, LeetCode, Easy, Tree, Depth-first Search, Breadth-first Search]
author: wchen02
excerpt_separator: <!--more-->
---
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

<!--more-->

For example, this binary tree `[1,2,2,3,4,4,3]` is symmetric:
<pre>
    1
   / \
  2   2
 / \ / \
3  4 4  3
</pre>

But the following `[1,2,2,null,3,null,3]` is not:
<pre>
    1
   / \
  2   2
   \   \
   3    3
</pre>

**Note**:
Bonus points if you could solve it both recursively and iteratively.

## Solution

```python
import collections

class TreeNode:
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None

class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        nodeQueue = collections.deque()

        if root != None:
            nodeQueue.append(root)

        while nodeQueue:
            innerLevel = []
            for _ in range(len(nodeQueue)):
                cur = nodeQueue.popleft()
                if cur:
                    innerLevel.append(cur.val)
                else:
                    innerLevel.append(None)

                if cur:
                    nodeQueue.append(cur.left)
                    nodeQueue.append(cur.right)

            innerEnd = len(innerLevel) - 1
            if cur != root and len(innerLevel) % 2 == 1:
                return False

            for j in range(len(innerLevel)//2):
                if innerLevel[j] != innerLevel[innerEnd-j]:
                    return False

        return True
```

## Test Cases

```python
test = Solution()
root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(2)
root.left.left = TreeNode(3)
root.left.right = TreeNode(4)
root.right.left = TreeNode(4)
root.right.right = TreeNode(3)
assert test.isSymmetric(root) == True

root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(2)
root.left.left = None
root.left.right = TreeNode(3)
root.right.left = None
root.right.right = TreeNode(3)
assert test.isSymmetric(root) == False

root = None
assert test.isSymmetric(root) == True
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(N)

**Time Complexity**: O(N)
