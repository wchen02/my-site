---
layout: post
title: 724. Find Pivot Index
tags: [Python, LeetCode, Easy, Array]
author-id: wchen02
excerpt_separator: <!--more-->
---

Given an array of integers `nums`, write a method that returns the "pivot" index of this array.

We define the pivot index as the index where the sum of the numbers to the left of the index is equal to the sum of the numbers to the right of the index.

If no such index exists, we should return -1. If there are multiple pivot indexes, you should return the left-most pivot index.
<!--more-->

**Example 1**:
> **Input**: 
> nums = [1, 7, 3, 6, 5, 6]
>
> **Output**: 3
>
> **Explanation**: 
> The sum of the numbers to the left of index 3 (nums[3] = 6) is equal to > the sum of numbers to the right of index 3.
> Also, 3 is the first index where this occurs.

**Example 2**:
> **Input**: 
> nums = [1, 2, 3]
>
> **Output**: -1
>
> **Explanation**: 
> There is no index that satisfies the conditions in the problem statement.

**Note**:

- The length of `nums` will be in the range `[0, 10000]`.
- Each element `nums[i]` will be an integer in the range `[-1000, 1000]`.

## Solution
```python
from typing import List

class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        rightSum = sum(nums)
        leftSum = 0
        for idx, num in enumerate(nums):
            leftSum += num
            if leftSum == rightSum:
                return idx
            rightSum -= num

        return -1
```

## Test Cases
```python
test = Solution()
answer = test.pivotIndex([1,2,3,4,6])
assert answer == 3
answer = test.pivotIndex([-1,1,-2,2,3,4,-4])
assert answer == 4
answer = test.pivotIndex([-1,1,-2,2,-3,3,4,-4])
assert answer == -1
answer = test.pivotIndex([-1,-1,0,0,-1,-1])
assert answer == 2
answer = test.pivotIndex([1,2,1])
assert answer == 1
answer = test.pivotIndex([1,2])
assert answer == -1
answer = test.pivotIndex([1])
assert answer == 0
answer = test.pivotIndex([])
assert answer == -1
print('All Passed!')
```

## Big O Analysis
**Space Complexity**: O(1)

**Time Complexity**: O(N)