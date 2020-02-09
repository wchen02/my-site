---
layout: post
title: 108. Convert Sorted Array to Binary Search Tree
tags: [Python, LeetCode, Easy, Tree, Depth-first Search]
author: wchen02
excerpt_separator: <!--more-->
---
Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

<!--more-->

**Example**:
> **Input**: [-10,-3,0,5,9]
>
> **Output**: [0,-3,9,-10,null,5]
>
> **Explanation**: One possible answer is: [0,-3,9,-10,null,5], which represents the following height balanced BST:
>
> <pre>
>       0
>      / \
>    -3   9
>    /   /
>  -10  5
> </pre>

## Solution

```python
from typing import List

class TreeNode:
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None

class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> TreeNode:
        if not nums:
            return None

        mid = int(len(nums) / 2)
        root = TreeNode(nums[mid])
        root.left = self.sortedArrayToBST(nums[:mid])
        root.right = self.sortedArrayToBST(nums[mid+1:])

        return root
```

## Test Cases

```python
test = Solution()
answer = test.sortedArrayToBST([-10,-3,0,5,9])
assert answer.val == 0
assert answer.left.val == -3
assert answer.left.left.val == -10
assert answer.right.val == 9
assert answer.right.left.val == 5

answer = test.sortedArrayToBST([-10,-3,0,5])
assert answer.val == 0
assert answer.left.val == -3
assert answer.left.left.val == -10
assert answer.right.val == 5

answer = test.sortedArrayToBST(None)
assert answer == None
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(log N)

**Time Complexity**: O(N), N = number of node
