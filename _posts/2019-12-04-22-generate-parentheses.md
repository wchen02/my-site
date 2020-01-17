---
layout: post
title: 22. Generate Parentheses
tags: [Python, LeetCode, Medium, String, Backtracking]
author-id: wchen02
excerpt_separator: <!--more-->
---
Given *n* pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

<!--more-->

**Example**:
> **Input**: 3
>
> **Output**:
>
> <pre>
> [
>   "((()))",
>   "(()())",
>   "(())()",
>   "()(())",
>   "()()()"
> ]
> </pre>

## Solution

```python
from typing import List

class Solution:
    def generateParenthesisHelper(self, parenthesis: [str], curStr: str, openParens: int, closeParens: int) -> None:
        if openParens == 0 and closeParens == 0:
            parenthesis.append(curStr)
            return

        if openParens > 0:
            self.generateParenthesisHelper(parenthesis, curStr + '(', openParens-1, closeParens)

        if closeParens > openParens:
            self.generateParenthesisHelper(parenthesis, curStr + ')', openParens, closeParens-1)

    def generateParenthesis(self, n: int) -> List[str]:
        parenthesis = []
        self.generateParenthesisHelper(parenthesis, "", n, n)
        return parenthesis
```

## Test Cases

```python
test = Solution()
answer = test.generateParenthesis(3)
assert answer == [
    "((()))",
    "(()())",
    "(())()",
    "()(())",
    "()()()"
], answer
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(1)

**Time Complexity**: O(2<sup>N</sup>)
