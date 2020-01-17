---
layout: post
title: 62. Unique Paths
tags: [Python, LeetCode, Medium, Array, Dynamic Programming]
author-id: wchen02
excerpt_separator: <!--more-->
---
A robot is located at the top-left corner of a *m* x *n* grid (marked 'Start' in the diagram below).

<!--more-->

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

![Diagonal Traverse]({{ "/assets/img/posts/robot_maze.png.png" | relative_url}})
<small>Above is a 7 x 3 grid. How many possible unique paths are there?</small>

**Note**: *m* and *n* will be at most 100.

**Example 1**:
> **Input**: m = 3, n = 2
>
> **Output**: 3
>
> **Explanation**: From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
>
> 1. Right -> Right -> Down
> 2. Right -> Down -> Right
> 3. Down -> Right -> Right

**Example 2**:
> **Input**: m = 7, n = 3
>
> **Output**: 28

## Solution

```python
from typing import List

class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        if m <= 1 or n <= 1:
            return 1

        path = [[1 for i in range(m)] for j in range(n)]

        for i in range(n-2, -1, -1):
            for j in range(m-2, -1, -1):
                path[i][j] = path[i+1][j] + path[i][j+1]
        return path[0][0]
```

## Test Cases

```python
test = Solution()
assert test.uniquePaths(3, 2) == 3
assert test.uniquePaths(7, 3) == 28
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(NM)

**Time Complexity**: O(NM)
