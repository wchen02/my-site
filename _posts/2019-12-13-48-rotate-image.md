---
layout: post
title: 48. Rotate Image
tags: [Python, LeetCode, Medium, Array]
author: wchen02
excerpt_separator: <!--more-->
---
You are given an *n* x *n* 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

<!--more-->

**Note**:

You have to rotate the image **in-place**, which means you have to modify the input 2D matrix directly. **DO NOT** allocate another 2D matrix and do the rotation.

**Example 1**:
> **Input**:
> <pre>
> [
>   [1,2,3],
>   [4,5,6],
>   [7,8,9]
> ]
> </pre>
>
> **Output**:
> <pre>
> [
>   [7,4,1],
>   [8,5,2],
>   [9,6,3]
> ]
> </pre>

**Example 1**:
> **Input**:
> <pre>
> [
>   [ 5, 1, 9,11],
>   [ 2, 4, 8,10],
>   [13, 3, 6, 7],
>   [15,14,12,16]
> ]
> </pre>
>
> **Output**:
> <pre>
> [
>   [15,13, 2, 5],
>   [14, 3, 4, 1],
>   [12, 6, 8, 9],
>   [16, 7,10,11]
> ]
> </pre>

## Solution

```python
from typing import List

class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        n = len(matrix[0])
        # transpose matrix
        for i in range(n):
            for j in range(i, n):
                matrix[j][i], matrix[i][j] = matrix[i][j], matrix[j][i]

        # reverse each row
        for i in range(n):
            matrix[i].reverse()
```

## Test Cases

```python
test = Solution()
matrix = [
    [1,2,3],
    [4,5,6],
    [7,8,9]
]
test.rotate(matrix)
assert matrix == [
    [7,4,1],
    [8,5,2],
    [9,6,3]
]
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(1)

**Time Complexity**: O(N<sup>2</sup>)
