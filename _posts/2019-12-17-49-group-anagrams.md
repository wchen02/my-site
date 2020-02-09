---
layout: post
title: 49. Group Anagrams
tags: [Python, LeetCode, Medium, Hash Table, String]
author: wchen02
excerpt_separator: <!--more-->
---
Given an array of strings, group anagrams together.

<!--more-->

**Example**:
> **Input**: ["eat", "tea", "tan", "ate", "nat", "bat"]
>
> **Output**:
> <pre>
> [
>   ["ate","eat","tea"],
>   ["nat","tan"],
>   ["bat"]
> ]
> </pre>

**Note**:

- All inputs will be in lowercase.
- The order of your output does not matter.

## Solution

```python
from typing import List
from collections import defaultdict

class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        hashmap = defaultdict(list)

        for aStr in strs:
            hashmap[str(sorted(aStr))].append(aStr)

        return list(hashmap.values())
```

## Test Cases

```python
test = Solution()
answer = test.groupAnagrams(["eat", "tea", "tan", "ate", "nat", "bat"])
assert answer == [
  ["eat","tea","ate"],
  ["tan","nat"],
  ["bat"]
], answer
print('All Passed!')
```

## Big O Analysis

**Space Complexity**: O(NK)

**Time Complexity**: O(NK log K) where N is the length of the input array and K is the max length of words in the array
