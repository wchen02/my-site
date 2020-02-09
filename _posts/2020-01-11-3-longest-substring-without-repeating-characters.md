---
layout: post
title: 3. Longest Substring Without Repeating Characters
tags: [Python, LeetCode, Medium, Hash Table, Two Pointers, String, Sliding Window]
author: wchen02
excerpt_separator: <!--more-->
---
Given a string, find the length of the **longest substring** without repeating characters.

<!--more-->

**Example 1**:
> **Input**: "abcabcbb"
>
> **Output**: 3
>
> **Explanation**: The answer is "abc", with the length of 3.

**Example 2**:
> **Input**: "bbbbb"
>
> **Output**: 1
>
> **Explanation**: The answer is "b", with the length of 1.

**Example 3**:
> **Input**: "pwwkew"
>
> **Output**: 3
>
> **Explanation**: The answer is "wke", with the length of 3.
>
> **Note**: The answer must be a substring, "pwke" is a subsequence and not a substring.

## Solution

```python
from typing import List

class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        begin, end = 0, len(s)
        startPos, longest = 0, 0
        chars = [False] * 128

        while begin < end:
            ch = ord(s[begin])
            if not chars[ch]:
                chars[ch] = True
                begin += 1
            else:
                longest = max(longest, begin - startPos)
                while chars[ch]:
                    startPosCh = ord(s[startPos])
                    chars[startPosCh] = False
                    startPos += 1
        return max(longest, begin - startPos)
```

## Test Cases

```python
test = Solution()
assert test.lengthOfLongestSubstring("abcabcbb") == 3
assert test.lengthOfLongestSubstring("bbbbb") == 1
assert test.lengthOfLongestSubstring("pwwkew") == 3
assert test.lengthOfLongestSubstring("") == 0
assert test.lengthOfLongestSubstring("a") == 1
assert test.lengthOfLongestSubstring(" ") == 1
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(1)

**Time Complexity**: O(N)
