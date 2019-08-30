---
layout: post
title: 498. Diagonal Traverse
tags: [Python, LeetCode, Medium, Array]
author-id: wchen02
excerpt_separator: <!--more-->
---

Given a matrix of M x N elements (M rows, N columns), return all elements of the matrix in diagonal order as shown in the below image.
<!--more-->

**Example**:
> **Input**: 
> [
>   [ 1, 2, 3 ],
>   [ 4, 5, 6 ],
>   [ 7, 8, 9 ]
> ]
>
> **Output**: 
> [1, 2, 4, 7, 5, 3, 6, 8, 9]
>
> **Explanation**: 
![Diagonal Traverse]({{ "/assets/img/posts/diagonal_traverse.png" | relative_url}})

**Note**:

The total number of elements of the given matrix will not exceed 10,000.

## Solution
```python
from typing import List

class Solution:
    def findDiagonalOrder(self, matrix: List[List[int]]) -> List[int]:
        if not matrix:
            return []

        result = []
        
        # Row and Col Directions
        directions = [
            [-1, 1],
            [1, -1],
        ]

        # Index to directions
        curDir = 0
        curRow = 0
        curCol = 0
        numRows = len(matrix)
        numCols = len(matrix[0])

        for i in range(numRows * numCols):
            result.append(matrix[curRow][curCol])

            # Top right corner
            if curRow + directions[curDir][0] < 0 and curCol + directions[curDir][1] == numCols:
                curRow += 1
                curDir = (curDir + 1) % 2
            # Bottom left corner
            elif curCol + directions[curDir][1] < 0 and curRow + directions[curDir][0] == numRows:
                curCol += 1
                curDir = (curDir + 1) % 2
            # Left or right border
            elif curCol + directions[curDir][1] == numCols or curCol + directions[curDir][1] < 0:
                curRow += 1
                curDir = (curDir + 1) % 2
            # Top or bottom border
            elif curRow + directions[curDir][0] == numRows or curRow + directions[curDir][0] < 0:
                curCol += 1
                curDir = (curDir + 1) % 2
            else:
                curRow += directions[curDir][0]
                curCol += directions[curDir][1]

        return result
```

## Test Cases
```python
test = Solution()
answer = test.findDiagonalOrder([])
assert answer == []
answer = test.findDiagonalOrder([[0]])
assert answer == [0]
answer = test.findDiagonalOrder([
    [1,2,3],
    [4,5,6],
    [7,8,9],
])
assert answer == [1,2,4,7,5,3,6,8,9]
answer = test.findDiagonalOrder([
    [1,2,3],
    [4,5,6],
])
assert answer == [1,2,4,5,3,6]
answer = test.findDiagonalOrder([
    [1,2,3],
])
assert answer == [1,2,3]
answer = test.findDiagonalOrder([
    [1,2],
    [4,5],
    [7,8],
])
assert answer == [1,2,4,7,5,8]
answer = test.findDiagonalOrder([
    [1],
    [4],
    [7],
])
assert answer == [1,4,7]
print('All Passed!')
```

## Big O Analysis
**Space Complexity**: O(1)

**Time Complexity**: O(MN) where M = number of row and N = number of columns 