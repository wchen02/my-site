---
layout: post
title: 169. Majority Element
tags: [Python, LeetCode, Easy, Array, Divide and Conquer, Bit Manipulation]
author-id: wchen02
excerpt_separator: <!--more-->
---
Given an array of size *n*, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

You may assume that the array is non-empty and the majority element always exist in the array.

<!--more-->
**Example 1**:
> **Input**: [3,2,3]
>
> **Output**: 3

**Example 2**:
> **Input**: [2,2,1,1,1,2,2]
>
> **Output**: 2

## Solution
```python
from typing import List, Dict

class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        numFreqMap = {}
        maxNum = 0
        maxCount = 0
        
        for i in range(len(nums)):
            if not numFreqMap.get(nums[i]):
                numFreqMap[nums[i]] = 1
            else:
                numFreqMap[nums[i]] += 1

        for k in numFreqMap.keys():
            if numFreqMap.get(k) > maxCount:
                maxNum = k
                maxCount = numFreqMap.get(k)

        return maxNum
```

## Test Cases
```python
test = Solution()
answer = test.majorityElement([0,1,0,0,3])
assert answer == 0,answer

answer = test.majorityElement([0,1,0])
assert answer == 0

answer = test.majorityElement([2,2,1,1,1,2,2])
assert answer == 2
print('All Passed!')
```

## Big O Analysis
**Space Complexity**: O(N)

**Time Complexity**: O(N)
