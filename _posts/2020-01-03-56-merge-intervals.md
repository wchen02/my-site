---
layout: post
title: 56. Merge Intervals
tags: [Python, LeetCode, Medium, Array, Sort]
author: wchen02
excerpt_separator: <!--more-->
---
Given a collection of intervals, merge all overlapping intervals.

<!--more-->

**Example 1**:
> **Input**: [[1,3],[2,6],[8,10],[15,18]]
>
> **Output**: [[1,6],[8,10],[15,18]]
>
> **Explanation**: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].

**Example 2**:
> **Input**: [[1,4],[4,5]]
>
> **Output**: [[1,5]]
>
> **Explanation**: Intervals [1,4] and [4,5] are considered overlapping.

**NOTE**: input types have been changed on April 15, 2019. Please reset to default code definition to get new method signature.

## Solution

```python
from typing import List

class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        if not intervals: return []
        intervals.sort(key = lambda n: n[0])
        result = [intervals[0]]

        for i in range(1, len(intervals)):
            if result[-1][1] >= intervals[i][0]:
                result[-1][1] = max(result[-1][1], intervals[i][1])
            else:
                result.append(intervals[i])

        return result
```

## Test Cases

```python
test = Solution()
assert test.merge([[1,3],[2,6],[8,10],[15,18]]) == [[1,6],[8,10],[15,18]]
assert test.merge([[1,4],[4,5]]) == [[1,5]]
assert test.merge([]) == []
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(1)

**Time Complexity**: O(N log N)
