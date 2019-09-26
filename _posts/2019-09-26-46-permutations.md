---
layout: post
title: 46. Permutations
tags: [Python, LeetCode, Medium, Backtracking]
author-id: wchen02
excerpt_separator: <!--more-->
---
Given a collection of **distinct** integers, return all possible permutations.
<!--more-->
**Example**:
> **Input**: 
> [1, 2, 3]
> 
> **Output**: 
> <pre>
> [
>   [1,2,3],
>   [1,3,2],
>   [2,1,3],
>   [2,3,1],
>   [3,1,2],
>   [3,2,1]
> ]
> </pre>

## Solution
```python
from typing import List

class Solution:
    def swap(self, nums: List[int], a, b):
        c = nums[a]
        nums[a] = nums[b]
        nums[b] = c

    def permute(self, nums: List[int]) -> List[List[int]]:
        permutations = []
        self.permuteStep(permutations, nums, 0)
        return permutations

    def permuteStep(self, permutations: List[List[int]], nums: List[int], index) -> None:
        if index == len(nums):
            permutations.append(nums.copy())

        for i in range(index, len(nums)):
            self.swap(nums, index, i)
            self.permuteStep(permutations, nums, index + 1)
            self.swap(nums, index, i)
```

## Test Cases
```python
test = Solution()
answer = test.permute([1,2,3])
answer.sort()
assert answer == [
    [1,2,3],
    [1,3,2],
    [2,1,3],
    [2,3,1],
    [3,1,2],
    [3,2,1]
]

answer = test.permute([1])
assert answer == [[1]]

answer = test.permute([])
assert answer == [[]]

answer = test.permute([1,2,3,4])
answer.sort()
assert answer == [
    [1,2,3,4],
    [1,2,4,3],
    [1,3,2,4],
    [1,3,4,2],
    [1,4,2,3],
    [1,4,3,2],
    [2,1,3,4],
    [2,1,4,3],
    [2,3,1,4],
    [2,3,4,1],
    [2,4,1,3],
    [2,4,3,1],
    [3,1,2,4],
    [3,1,4,2],
    [3,2,1,4],
    [3,2,4,1],
    [3,4,1,2],
    [3,4,2,1],
    [4,1,2,3],
    [4,1,3,2],
    [4,2,1,3],
    [4,2,3,1],
    [4,3,1,2],
    [4,3,2,1]
]
print('All Passed!')
```

## Big O Analysis
**Space Complexity**: O(N!)

**Time Complexity**: O(N!)
