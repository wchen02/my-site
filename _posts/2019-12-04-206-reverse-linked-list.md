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
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None

class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        if head == None:
            return None

        oldHead = head
        newHead = head.next
        oldHead.next = None

        while newHead:
            newHead2 = newHead.next
            newHead.next = oldHead
            oldHead = newHead
            newHead = newHead2
        
        return oldHead
```

## Test Cases
```python
test = Solution()
testHead = ListNode(1)
testHead.next = ListNode(2)
testHead.next.next = ListNode(3)
answer = test.reverseList(testHead)
assert answer.val == 3
assert answer.next.val == 2
assert answer.next.next.val == 1

answer = test.reverseList(None)
assert answer == None
print('All Passed!')
```

## Big O Analysis
**Space Complexity**: O(1)

**Time Complexity**: O(N)
