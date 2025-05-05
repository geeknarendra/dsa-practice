# 790. Domino And Tromino Tiling

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/domino-and-tromino-tiling/description/?envType=daily-question&envId=2025-05-05)

## Solution

```python
class Solution:
##############################################################################
    # Iterative Dynamic Programming approach
    def numTilings(self, n: int) -> int:
        # Base cases:
        # n = 1: Only 1 way → [1 vertical domino]
        # n = 2: Two ways → [2 vertical dominos] or [2 horizontal dominos]
        # n = 3: 5 ways (as per problem example)
        if n <= 2:
            return n
        if n == 3:
            return 5

        MOD = 10**9 + 7
        dp = [-1] * (n + 1)

        # Initialize base values
        dp[1], dp[2], dp[3] = 1, 2, 5

        # Recurrence relation:
        # dp[i] = 2 * dp[i - 1] + dp[i - 3]
        #
        # Explanation of the recurrence:
        # 1. 2 * dp[i - 1]:
        #    - Case 1: Add a vertical domino to all dp[i-1] configurations
        #    - Case 2: Add an L-shaped tromino to dp[i-1] in two orientations
        #
        # 2. dp[i - 3]:
        #    - Special configurations where a tromino and domino overlap in a zig-zag
        #      pattern (like a staircase) spanning 3 columns, creating new tiling patterns
        for i in range(4, n + 1):
            dp[i] = (2 * dp[i - 1] + dp[i - 3]) % MOD

        return dp[n]

###########################################################################
# Recursive + Memoization approach
    def numTilings(self, n: int) -> int:
        MOD = 10**9 + 7
        memo = [-1] * (n + 1)
        return self._solve(n, memo, MOD)

    def _solve(self, n: int, memo: list[int], MOD: int) -> int:
        # Base cases as before
        if n <= 2:
            return n
        if n == 3:
            return 5

        # If already computed, return from memo
        if memo[n] != -1:
            return memo[n]

        # Apply recurrence:
        # T(n) = 2 * T(n - 1) + T(n - 3)
        #
        # Where:
        # - T(n - 1): Add vertical domino or L-tromino
        # - T(n - 3): Special cases (combinations like 2 dominos + tromino etc.)
        memo[n] = (2 * self._solve(n - 1, memo, MOD) + self._solve(n - 3, memo, MOD)) % MOD
        return memo[n]

```

## Additional Test Cases  
Copy and paste directly into LeetCode custom test editor:
```
1
5
6
7
100
500
999
1000
```
