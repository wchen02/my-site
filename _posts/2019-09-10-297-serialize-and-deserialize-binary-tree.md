---
layout: post
title: 297. Serialize and Deserialize Binary Tree
tags: [Python, LeetCode, Hard, Tree, Design]
author-id: wchen02
excerpt_separator: <!--more-->
---
Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.
<!--more-->

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

**Example**:
> **Input**:
> `[1, 2, 3, null, null, 4, 5]`,
> <pre>
>     1
>    / \
>   2  3
>     /  \
>    4    5
> </pre>
>
> **Output**: "[1,2,3,null,null,4,5]"

**Clarification**: The above format is the same as how LeetCode serializes a binary tree. You do not necessarily need to follow this format, so please be creative and come up with different approaches yourself.

**Note**: Do not use class member/global/static variables to store states. Your serialize and deserialize algorithms should be stateless.

## Solution

```python
from collections import deque

class TreeNode:
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None

class Codec:

    # Encodes a tree to a single string.
    def serialize(self, root: TreeNode) -> str:
        if not root:
            return '[]'

        result = []
        q = deque([root])

        while q:
            node = q.popleft()
            if node:
                result.append(str(node.val))
                q.append(node.left)
                q.append(node.right)
            else:
                result.append('null')

        while result and result[-1] == 'null' and result[-2] == 'null':
            result.pop()
            result.pop()

        return '[' + ','.join(result) + ']'

    # Decodes your encoded data to tree.
    def deserialize(self, data: str) -> TreeNode:
        if data == '[]':
            return None

        nodes = data[1:-1].split(',')
        root = TreeNode(nodes[0])
        q = deque([root])
        i = 1

        while i + 1 < len(nodes):
            node = q.popleft()
            if nodes[i] != 'null':
                node.left =  TreeNode(nodes[i])
                q.append(node.left)

            if nodes[i+1] != 'null':
                node.right = TreeNode(nodes[i+1])
                q.append(node.right)

            i += 2

        return root
```

## Test Cases

```python
test = Codec()
node1 = TreeNode(1)
node2 = TreeNode(2)
node3 = TreeNode(3)
node4 = TreeNode(4)
node5 = TreeNode(5)
node6 = TreeNode(6)
node7 = TreeNode(7)
node8 = TreeNode(8)
node9 = TreeNode(9)

serialized1 = test.serialize(None)
deserialized1 = test.deserialize(serialized1)
serialized2 = test.serialize(deserialized1)
assert serialized1 == serialized2

node1.right = node2
node2.left = node3
serialized1 = test.serialize(node1)
deserialized1 = test.deserialize(serialized1)
serialized2 = test.serialize(deserialized1)
assert serialized1 == serialized2

node1.left = node2
node1.right = node3
node2.left = node4
node2.right = node5
node5.left = node8
node3.left = node6
node3.right = node7
node6.right = node9
serialized1 = test.serialize(node1)
deserialized1 = test.deserialize(serialized1)
serialized2 = test.serialize(deserialized1)
assert serialized1 == serialized2
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(N)

**Time Complexity**: O(N)

for both `serialize` and `deserialize` methods
