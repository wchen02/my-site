---
layout: post
title: 19. Remove Nth Node From End of List
tags: [Python, LeetCode, Medium, Linked List, Two Pointers]
author-id: wchen02
excerpt_separator: <!--more-->
---
Given a linked list, remove the *n*-th node from the end of list and return its head.

<!--more-->

**Example**:
> **Input**: **1->2->3->4->5** and **n = 2**
>
> **Output**: **1->2->3->5**

**Note**:

Given *n* will always be valid.

**Follow up**:

Could you do this in one pass?

## Solution

```python
from typing import List

class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None

class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        dummy = ListNode(0)
        dummy.next = head
        walker = dummy
        walker2 = dummy

        while n:
            walker = walker.next
            n -= 1

        while walker.next:
            walker2 = walker2.next
            walker = walker.next

        walker2.next = walker2.next.next
        return dummy.next
```

## Test Cases

```python
test = Solution()
head = ListNode(1)
head.next = ListNode(2)
head.next.next = ListNode(3)
head.next.next.next = ListNode(4)
head.next.next.next.next = ListNode(5)

answer = test.removeNthFromEnd(head, 1)
assert answer.val == 1
assert answer.next.val == 2
assert answer.next.next.val == 3
assert answer.next.next.next.val == 4

head = ListNode(1)
head.next = ListNode(2)
head.next.next = ListNode(3)
head.next.next.next = ListNode(4)
head.next.next.next.next = ListNode(5)

answer = test.removeNthFromEnd(head, 2)
assert answer.val == 1
assert answer.next.val == 2
assert answer.next.next.val == 3
assert answer.next.next.next.val == 5

head = ListNode(1)
head.next = ListNode(2)

answer = test.removeNthFromEnd(head, 2)
assert answer.val == 2

head = ListNode(1)
answer = test.removeNthFromEnd(head, 1)
assert answer == None
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(1)

**Time Complexity**: O(N)
