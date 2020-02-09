---
layout: post
title: 73. Set Matrix Zeroes
tags: [Python, LeetCode, Medium, Array]
author: wchen02
excerpt_separator: <!--more-->
---
Given a *m* x *n* matrix, if an element is 0, set its entire row and column to 0. Do it **in-place**.

<!--more-->

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

**Example 1**:
> **Input**:
> <pre>
> [
>   [1,1,1],
>   [1,0,1],
>   [1,1,1]
> ]
> </pre>
>
> **Output**:
> <pre>
> [
>   [1,0,1],
>   [0,0,0],
>   [1,0,1]
> ]
> </pre>

**Example 2**:
> **Input**:
> <pre>
> [
>   [0,1,2,0],
>   [3,4,5,2],
>   [1,3,1,5]
> ]
> </pre>
>
> **Output**:
> <pre>
> [
>   [0,0,0,0],
>   [0,4,5,0],
>   [0,3,1,0]
> ]
> </pre>

**Follow up**:

- A straight forward solution using O(mn) space is probably a bad idea.
- A simple improvement uses O(m + n) space, but still not the best solution.
- Could you devise a constant space solution?

## Solution

```python
from typing import List

class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        if not matrix or not matrix[0]:
            return

        rows, cols = len(matrix), len(matrix[0])
        isRowZero, isColZero = False, False

        for row in range(rows):
            for col in range(cols):
                if matrix[row][col] == 0:
                    if row == 0: isRowZero = True
                    if col == 0: isColZero = True
                    matrix[0][col] = 0
                    matrix[row][0] = 0

        for row in range(1, rows):
            for col in range(1, cols):
                if matrix[0][col] == 0 or matrix[row][0] == 0:
                    matrix[row][col] = 0

        if isRowZero:
            for col in range(cols):
                matrix[0][col] = 0

        if isColZero:
            for row in range(rows):
                matrix[row][0] = 0
```

## Test Cases

```python
test = Solution()
matrix = [
  [1,1,1],
  [1,0,1],
  [1,1,1]
]
test.setZeroes(matrix)
assert matrix == [
  [1,0,1],
  [0,0,0],
  [1,0,1]
]

matrix = [
  [0,1,2,0],
  [3,4,5,2],
  [1,3,1,5]
]
test.setZeroes(matrix)
assert matrix == [
  [0,0,0,0],
  [0,4,5,0],
  [0,3,1,0]
]

matrix = []
test.setZeroes(matrix)
assert matrix == []

matrix = [[]]
test.setZeroes(matrix)
assert matrix == [[]]
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(1)

**Time Complexity**: O(MN), where M is number of rows and N is number of cols
