---
layout: post
title: 11. Container With Most Water
tags: [Python, LeetCode, Medium, Array, Two Pointers]
author-id: wchen02
excerpt_separator: <!--more-->
---
Given *n* non-negative integers *a<sub>1</sub>*, *a<sub>2</sub>*, ..., *a<sub>n</sub>* , where each represents a point at coordinate (*i*, *a<sub>i</sub>*). n vertical lines are drawn such that the two endpoints of line i is at (*i*, *a<sub>i</sub>*) and (*i*, *0*). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

<!--more-->

**Note**: You may not slant the container and *n* is at least 2.

![Container With Most Water]({{ "/assets/img/posts/question_11.jpg" | relative_url}})

<small>The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.</small>

**Example**:
> **Input**: [1,8,6,2,5,4,8,3,7]
>
> **Output**: 49

## Solution

```python
from typing import List

class Solution:
    def maxArea(self, height: List[int]) -> int:
        left, right = 0, len(height) - 1
        maxArea = 0

        while left < right:
            area = (right-left) * min(height[left], height[right])
            maxArea = max(maxArea, area)
            if height[left] < height[right]:
                left += 1
            else:
                right -= 1

        return maxArea
```

## Test Cases

```python
test = Solution()
assert test.maxArea([1,8,6,2,5,4,8,3,7]) == 49
assert test.maxArea([1,2]) == 1
assert test.maxArea([2,3,4,5,18,17,6]) == 17
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(1)

**Time Complexity**: O(N)
