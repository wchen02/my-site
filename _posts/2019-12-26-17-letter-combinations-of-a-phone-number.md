---
layout: post
title: 17. Letter Combinations of a Phone Number
tags: [Python, LeetCode, Medium, String, Backtracking]
author-id: wchen02
excerpt_separator: <!--more-->
---
Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent.

<!--more-->

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

![Container With Most Water]({{ "/assets/img/posts/200px-Telephone-keypad2.svg.png" | relative_url}})

**Example**:
> **Input**: "23"
>
> **Output**: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
>
> **Explanation**: The answer is "abc", with the length of 3.

**Note**:

Although the above answer is in lexicographical order, your answer could be in any order you want.

## Solution

```python
from typing import List

class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        def helper(curString: List[str], i: int) -> None:
            nonlocal digitLetterMap, combos

            if i == len(digits):
                combos.append("".join(curString))
                return

            for letter in digitLetterMap[int(digits[i])]:
                curString[i] = letter
                helper(curString, i+1)

        if not digits: return []
        digitLetterMap = ['0','1','abc','def','ghi','jkl','mno','pqrs','tuv','wxyz']
        combos = []
        helper([None]*len(digits), 0)
        return combos
```

## Test Cases

```python
test = Solution()
assert test.letterCombinations('23') == [
    "ad",
    "ae",
    "af",
    "bd",
    "be",
    "bf",
    "cd",
    "ce",
    "cf"
]
assert test.letterCombinations('') == []
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(4<sup>N</sup>)

**Time Complexity**: O(4<sup>N</sup>)
