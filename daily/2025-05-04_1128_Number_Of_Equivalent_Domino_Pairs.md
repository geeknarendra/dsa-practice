# 1128. Number Of Equivalent Domino Pairs

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/number-of-equivalent-domino-pairs/description/?envType=daily-question&envId=2025-05-04)

Given a list of dominoes, dominoes[i] = [a, b] is equivalent to dominoes[j] = [c, d] if and only if either (a == c and b == d), or (a == d and b == c) - that is, one domino can be rotated to be equal to another domino.

Return the number of pairs (i, j) for which 0 <= i < j < dominoes.length, and dominoes[i] is equivalent to dominoes[j].

## Solution

```python
class Solution:
    def numEquivDominoPairs(self, dominoes: List[List[int]]) -> int:

        res=0
        # Let calculate a val by x*10+y where x is smaller than y
        pairs_cnt=[0]*100

        for x,y in dominoes:
            val = x*10+y if x<y else y*10+x

            res+=pairs_cnt[val]
            pairs_cnt[val]+=1

        return res

######################################################
# Time - O(n)
# Space -
        res=0
        pairs_cnt=defaultdict(int)

        for domino in dominoes:
            domino=tuple(sorted(domino))

            res+=pairs_cnt[domino]
            pairs_cnt[domino]+=1

        return res

        
```

## Additional Test Cases  
Copy and paste directly into LeetCode custom test editor:
```
[[1,8],[8,1],[1,8],[1,8],[1,8],[8,1],[8,2],[8,1],[8,1]]
[[8,8],[8,8],[8,8],[8,8],[8,8],[8,8],[8,8],[8,8],[8,8]]
[[1,2],[1,3],[1,4],[1,5],[1,6],[1,7],[1,8],[1,9]]
[[8,8]]
[[1,8]]
[[8,1],[1,8]]
```
