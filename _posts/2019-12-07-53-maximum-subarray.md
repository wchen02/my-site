---
layout: post
title: 53. Maximum Subarray
tags: [Python, LeetCode, Easy, Array, Divide and Conquer, Dynamic Programming]
author-id: wchen02
excerpt_separator: <!--more-->
---
Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

<!--more-->
**Example**:
> **Input**: [-2,1,-3,4,-1,2,1,-5,4]
>
> **Output**: 6
>
> **Explanation**: [4,-1,2,1] has the largest sum = 6.

**Follow up**:

If you have figured out the O(*n*) solution, try coding another solution using the divide and conquer approach, which is more subtle.

## Solution
```python
import sys
from typing import List

class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        maxSum = -sys.maxsize-1
        curSum = -sys.maxsize-1

        for i in range(len(nums)):
            curSum = max(nums[i], curSum + nums[i])
            maxSum = max(curSum, maxSum)

        return maxSum
```

## Test Cases
```python
test = Solution()
answer = test.maxSubArray([-2,1,-3,4,-1,2,1,-5,4])
assert answer == 6
answer = test.maxSubArray([-2])
assert answer == -2
answer = test.maxSubArray([-2,-3])
assert answer == -2
print('All Passed!')
```

## Big O Analysis
**Space Complexity**: O(1)

**Time Complexity**: O(N)
