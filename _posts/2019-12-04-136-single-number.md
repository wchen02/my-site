---
layout: post
title: 136. Single Number
tags: [Python, LeetCode, Easy, Hash Table, Bit Manipulation]
author-id: wchen02
excerpt_separator: <!--more-->
---
Given a **non-empty** array of integers, every element appears twice except for one. Find that single one.

<!--more-->
**Note**:

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?


**Example 1**:
> **Input**: [2, 2, 1]
>
> **Output**: 1

**Example 2**:
> **Input**: [4, 1, 2, 1, 2]
>
> **Output**: 4

## Solution
```python
from typing import List

class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        result = 0
        
        for i in range(len(nums)):
            result ^= nums[i]

        return result
```

## Test Cases
```python
test = Solution()
answer = test.singleNumber([1,1,2,4,2,3,3])
assert answer == 4

answer = test.singleNumber([1])
assert answer == 1
print('All Passed!')
```

## Big O Analysis
**Space Complexity**: O(1)

**Time Complexity**: O(N)
