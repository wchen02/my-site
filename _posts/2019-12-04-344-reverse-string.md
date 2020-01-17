---
layout: post
title: 344. Reverse String
tags: [Python, LeetCode, Easy, Linked List]
author-id: wchen02
excerpt_separator: <!--more-->
---
Write a function that reverses a string. The input string is given as an array of characters `char[]`.

Do not allocate extra space for another array, you must do this by **modifying the input array** *in-place* with O(1) extra memory.

You may assume all the characters consist of printable ascii characters.

<!--more-->
**Example 1**:
> **Input**: ["h","e","l","l","o"]
>
> **Output**: ["o","l","l","e","h"]

**Example 1**:
> **Input**: ["H","a","n","n","a","h"]
>
> **Output**: ["h","a","n","n","a","H"]

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
