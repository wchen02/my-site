---
layout: post
title: 206. Reverse Linked List
tags: [Python, LeetCode, Easy, Linked List]
author-id: wchen02
excerpt_separator: <!--more-->
---
Reverse a singly linked list.

<!--more-->
**Example**:
> **Input**: 1->2->3->4->5->NULL
>
> **Output**: 5->4->3->2->1->NULL

**Follow up**:

A linked list can be reversed either iteratively or recursively. Could you implement both?

## Solution
```python
from typing import List

class Solution:
    def reverseString(self, s: List[str]) -> None:
        for i in range(int(len(s) / 2)):
            temp = s[i]
            s[i] = s[len(s) - 1 - i]
            s[len(s) - 1 - i] = temp
```

## Test Cases
```python
test = Solution()
testStr = ['a', 'b', 'c']
test.reverseString(testStr)
assert testStr == ['c', 'b', 'a']

testStr = []
test.reverseString(testStr)
assert testStr == []

testStr = ['a']
test.reverseString(testStr)
assert testStr == ['a']
print('All Passed!')
```

## Big O Analysis
**Space Complexity**: O(1)

**Time Complexity**: O(N)
