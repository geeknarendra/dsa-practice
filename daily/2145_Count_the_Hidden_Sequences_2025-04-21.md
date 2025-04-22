# 2145. Count the Hidden Sequences

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/count-the-hidden-sequences/description/)

Given a list of `differences` and two integers `lower` and `upper`, you need to find the number of valid hidden sequences that can be formed based on the differences. The hidden sequence is formed by starting from some integer `x` and then adding the differences successively. The sequence must be within the range `[lower, upper]`.

## Solution

```python
class Solution:
    def numberOfArrays(self, differences: List[int], lower: int, upper: int) -> int:
        n = len(differences)

        # Binary Search to find valid lower and upper bounds
        def isPossible(num):
            for i in range(n):
                num += differences[i]
                if num < lower:
                    return -1
                elif num > upper:
                    return 1
            return 0

        def lowerBound():
            l, r = lower, upper
            while l <= r:
                mid = (l + r) // 2
                if isPossible(mid) >= 0:
                    r = mid - 1
                else:
                    l = mid + 1
            return l

        def upperBound():
            l, r = lower, upper
            while l <= r:
                mid = (l + r) // 2
                if isPossible(mid) <= 0:
                    l = mid + 1
                else:
                    r = mid - 1
            return l

        return upperBound() - lowerBound()
```

## Additional Test Cases  
Copy and paste directly into LeetCode custom test editor:

```
[2, -2, 3, -3, 4, -4, 5, -5]
0
10
[1, -1, 2, -2, 3, -3, 4, -4, 5, -5]
-3
7
[3, -2, 1, -3, 2, -1, 3, -3]
1
8
[1, 1, 1, 1, 1, -5]
0
5
[5, -4, 3, -2, 1, -1, -2, 2, -3, 3]
-2
6
[1, 2, -1, -2, 3, -3, 4, -4, 5, -5]
0
10
[4, -4, 4, -4, 4, -4, 4, -4, 4]
-5
5
[-40]
-46
53
```

