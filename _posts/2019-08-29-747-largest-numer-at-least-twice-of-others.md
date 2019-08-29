---
layout: post
title: 724. Largest Number At Least Twice of Others
tags: [Python, LeetCode, Easy, Array]
author-id: wchen02
excerpt_separator: <!--more-->
---

In a given integer array `nums`, there is always exactly one largest element.

Find whether the largest element in the array is at least twice as much as every other number in the array.

If it is, return the **index** of the largest element, otherwise return -1.
<!--more-->

**Example 1**:
> **Input**: 
> nums = [3, 6, 1, 0]
>
> **Output**: 1
>
> **Explanation**: 
> 6 is the largest integer, and for every other number in the array x,
> 6 is more than twice as big as x.  The index of value 6 is 1, so we return 1.

**Example 2**:
> **Input**: 
> nums = [1, 2, 3, 4]
>
> **Output**: -1
>
> **Explanation**: 
> 4 isn't at least as big as twice the value of 3, so we return -1.

**Note**:

1. `nums` will have a length in the range `[1, 50]`.
2. Every `nums[i]` will be an integer in the range `[0, 99]`.


## Solution
```python
from typing import List

class Solution:
    def dominantIndex(self, nums: List[int]) -> int:
        largestNumIndex = -1
        largestNum = 0
        secondLargestNum = 0
        
        for index, num in enumerate(nums):
            if num >= largestNum:
                secondLargestNum = largestNum
                largestNum = num
                largestNumIndex = index
            elif num > secondLargestNum:
                secondLargestNum = num
        
        if largestNum >= secondLargestNum * 2:
            return largestNumIndex
        
        return -1
```

## Test Cases
```python
test = Solution()
answer = test.dominantIndex([1,2,3,4])
assert answer == -1
answer = test.dominantIndex([1])
assert answer == 0
answer = test.dominantIndex([1,2])
assert answer == 1
answer = test.dominantIndex([0,99])
assert answer == 1
answer = test.dominantIndex([0,0,3,2])
assert answer == -1
answer = test.dominantIndex([49,99])
assert answer == 1
print('All Passed!')
```

## Big O Analysis
**Space Complexity**: O(1)

**Time Complexity**: O(N)