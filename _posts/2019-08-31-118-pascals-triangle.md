---
layout: post
title: 118. Pascal's Triangle
tags: [Python, LeetCode, Easy, Array]
author-id: wchen02
excerpt_separator: <!--more-->
---

Given a non-negative integer *numRows*, generate the first *numRows* of Pascal's triangle.
<!--more-->
![Pascal's Triangle]({{ "/assets/img/posts/PascalTriangleAnimated2.gif" | relative_url}})

In Pascal's triangle, each number is the sum of the two numbers directly above it.


**Example**:
> **Input**: 
> 5
>
> **Output**: 
> <pre>
> [
>       [ 1 ],
>      [ 1, 1 ],
>     [ 1, 2, 1 ],
>    [ 1, 3, 3, 1 ],
>   [ 1, 4, 6, 4, 1 ]
> ]
> </pre>

## Solution
```python
from typing import List

class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        result = []

        for i in range(numRows):
            newList = [1] * (i+1)
            for j in range(1, len(newList) - 1):
                newList[j] = result[i-1][j-1] + result[i-1][j]
            result.append(newList)

        return result
```

## Test Cases
```python
test = Solution()
answer = test.generate(0)
assert answer == []
answer = test.generate(1)
assert answer == [[1]]
answer = test.generate(2)
assert answer == [[1],[1,1]]
answer = test.generate(5)
assert answer == [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
print('All Passed!')
```

## Big O Analysis
**Space Complexity**: O(1)

**Time Complexity**: O(N<sup>2</sup>)