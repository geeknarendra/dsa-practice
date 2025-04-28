# 3392. Count Subarrays of Length Three With a Condition

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/count-subarrays-of-length-three-with-a-condition/description/)

Given an integer array nums, return the number of subarrays of length 3 such that the sum of the first and third numbers equals exactly half of the second number.



## Solution

```python
class Solution:
    def countSubarrays(self, nums: List[int]) -> int:
        n=len(nums)
        res=0
        for i in range(n-2):
            if (nums[i]+nums[i+2])==(nums[i+1]/2):
                res+=1
        
        return res
         
```
