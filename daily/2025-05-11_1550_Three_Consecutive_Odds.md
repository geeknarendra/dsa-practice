# 1550. Three Consecutive Odds

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/three-consecutive-odds/description/?envType=daily-question&envId=2025-05-11)

Given an integer array arr, return true if there are three consecutive odd numbers in the array. Otherwise, return false.
 
## Solution

```python
class Solution:
    def threeConsecutiveOdds(self, arr: List[int]) -> bool:

# Brute Force - Checking consecutive 3 number for current index
   
        # for i in range(len(arr)-2):
        #     if arr[i]%2!=0 and arr[i+1]%2!=0 and arr[i+2]%2!=0:
        #         return True
        # return False

# Counting Consecutive Odds
        consecutive_odds=0

        for num in arr:
            if num%2==1:
                consecutive_odds+=1
            else:
                consecutive_odds=0
            
            if consecutive_odds==3:
                return True
        
        return False
```


