---
layout: post
title: 34. Find First and Last Position of Element in Sorted Array
tags: [Python, LeetCode, Medium, Array, Binary Search]
author: wchen02
excerpt_separator: <!--more-->
---
Given an array of integers `nums` sorted in ascending order, find the starting and ending position of a given `target` value.

<!--more-->

Your algorithm's runtime complexity must be in the order of O(log *n*).

If the target is not found in the array, return `[-1, -1]`.

**Example 1**:
> **Input**: nums = [5,7,7,8,8,10], target = 8
>
> **Output**: [3,4]

**Example 2**:
> **Input**: nums = [5,7,7,8,8,10], target = 6
>
> **Output**: [-1,-1]

## Solution

```python
from typing import List

class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        lo = 0
        hi = len(nums) - 1
        ret = [-1, -1]

        if not nums: return ret

        while lo < hi:
            mid = lo + (hi-lo) // 2

            if nums[mid] < target:
                lo = mid + 1
            else:
                hi = mid

        if nums[lo] == target:
            ret[0] = lo
        else:
            return ret

        hi = len(nums) - 1
        while lo < hi:
            mid = lo + (hi-lo) // 2 + 1

            if nums[mid] > target:
                hi = mid - 1
            else:
                lo = mid

        ret[1] = hi
        return ret
```

## Test Cases

```python
test = Solution()
assert test.searchRange([5,7,7,8,8,10], 8) == [3,4]
assert test.searchRange([5,7,7,8,8,10], 6) == [-1,-1]
assert test.searchRange([5,7,7,8,8,10], 5) == [0,0]
assert test.searchRange([5,7,7,8,8,10], 10) == [5,5]
assert test.searchRange([5,5,5,5,5,7,7,8,8,10], 5) == [0,4]
assert test.searchRange([5,5,5,5,5,7,7,8,8,10],7) == [5,6]
assert test.searchRange([],0) == [-1,-1]
assert test.searchRange([1],0) == [-1,-1]
assert test.searchRange([1],1) == [0,0]
assert test.searchRange([1,1],1) == [0,1]
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(1)

**Time Complexity**: O(log(N))
