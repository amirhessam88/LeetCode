## Problem: Max Subarray

## Difficulty: Medium

## Description:
Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of the line i is at (i, ai) and (i, 0). Find two lines, which, together with the x-axis forms a container, such that the container contains the most water.

## Solution 

```python
class Solution(object):
    def intToRoman(self, num):
        """
        :type num: int
        :rtype: str
        """
        dct = {1: 'I', 4: 'IV', 5: 'V', 9: 'IX', 10: 'X', 40: 'XL', 50: 'L', 90: 'XC', 100: 'C', 400: 'CD', 500: 'D', 900: 'CM', 1000: 'M'}
        stack = [1, 4, 5, 9, 10, 40, 50, 90, 100, 400, 500, 900, 1000]
        ans = []
        while num > 0:
            if stack[-1] > num:
                stack.pop()
            else:
                num -= stack[-1]
                ans.append(dct[stack[-1]])
        return "".join(map(str, ans))      

```

