## Problem: Subarray Sums Divisible by K

## Difficulty: Medium

## Description:
Given an array `A` of integers, return the number of (contiguous, non-empty) subarrays that have a sum divisible by `K`.

## Examples:
```
Input: A = [4,5,0,-2,-3,1], K = 5
Output: 7
Explanation: There are 7 subarrays with a sum divisible by K = 5:
[4, 5, 0, -2, -3, 1], [5], [5, 0], [5, 0, -2, -3], [0], [0, -2, -3], [-2, -3]
```

## Constraints:
```
1 <= A.length <= 30000
-10000 <= A[i] <= 10000
2 <= K <= 10000
```

## Solutions: 
The naive appraoch is always to produce all of the subarrays and find the one that meets the objective. This approach has a time complexity of `O(N^3)` and space complexity of `O(N)` where `N` is the size of array.

```python
def subarraysDivByK(A, K):
    """
    :type A: List[int]
    :type K: int
    :rtype: int
    :Time Complexity: O(N^3)
    :Space Complexity: O(N)
    """
    ans = 0

    for i in range(len(A)):
        for j in range(i, len(A)):
            sub = A[i : j + 1]
            if sum(sub) % K == 0:
                ans += 1
    return ans
```

For the optimal solution, we can use the Prefix-Sum algorithm. This approach has a time complexity of `O(N)` and space complexity of `O(N)` where `N` is the size of array.
 
```python
def subarraysDivByK(A, K):
    """
    :type A: List[int]
    :type K: int
    :rtype: int
    :Time Complexity: O(N)
    :Space Complexity: O(N)
    """
    ans = 0
    seen = {0: 1}
    current_sum = 0

    for i in range(len(A)):
        current_sum += A[i]
        key = current_sum % K

        if key in seen:
            ans += seen[key]
            seen[key] += 1
        else:
            seen[key] = 1

    return ans
```

