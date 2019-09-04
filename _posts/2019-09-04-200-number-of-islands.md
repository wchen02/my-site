---
layout: post
title: 200. Number of Islands
tags: [Python, LeetCode, Medium, Depth-first Search, Breadth-first Search, Union Find]
author-id: wchen02
excerpt_separator: <!--more-->
---

Given a 2d grid map of '`1`'s (land) and '`0`'s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.
<!--more-->

**Example 1**:
> **Input**: 
> <pre>
> 11110
> 11010
> 11000
> 00000
> </pre>
>
> **Output**: 
> 1

**Example 2**:
> **Input**: 
> <pre>
> 11000
> 11000
> 00100
> 00011
> </pre>
>
> **Output**: 
> 3

## Solution
```python
from typing import List

class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid:
            return 0

        numIslands = 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == '1':
                    self.dfs(grid, i, j)
                    numIslands += 1

        return numIslands

    def dfs(self, grid: List[List[str]], row, col) -> None:
        if row < 0 or row >= len(grid) or col < 0 or col >= len(grid[0]):
            return

        if grid[row][col] != '1':
            return

        grid[row][col] = '2'
        self.dfs(grid, row-1, col)
        self.dfs(grid, row+1, col)
        self.dfs(grid, row, col-1)
        self.dfs(grid, row, col+1)
```

## Test Cases
```python
test = Solution()
answer = test.numIslands([
    ['1', '1', '1', '1', '0'],
    ['1', '1', '0', '1', '0'],
    ['1', '1', '0', '0', '0'],
    ['0', '0', '0', '0', '0']
])
assert answer == 1
answer = test.numIslands([])
assert answer == 0
answer = test.numIslands([
    ['1', '1', '0', '0', '0'],
    ['1', '1', '0', '0', '0'],
    ['0', '0', '1', '0', '0'],
    ['0', '0', '0', '1', '1']
])
assert answer == 3
print('All Passed!')
```

## Big O Analysis
**Space Complexity**: O(1)

**Time Complexity**: O(N), N = number of cells
