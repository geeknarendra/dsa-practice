# 2962. Count Subarrays Where Max Element Appears At Least K Times

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/count-subarrays-where-max-element-appears-at-least-k-times/?envType=daily-question&envId=2025-04-29)

You are given an integer array nums and a positive integer k.

Return the number of subarrays where the maximum element of nums appears at least k times in that subarray.

A subarray is a contiguous sequence of elements within an array.

## Solution

```python
class Solution:
    def countSubarrays(self, nums: List[int], k: int) -> int:
        
        n=len(nums)
        maxNum=max(nums)
        res=0

        left=0
        maxEleCnt=0

        for right in range(n):
            if nums[right]==maxNum:
                maxEleCnt+=1
            
            while maxEleCnt>=k:
                #print(left,right,res)
                res+=(n-right)
                if nums[left]==maxNum:
                    maxEleCnt-=1
                left+=1
        
        return res


```

## Additional Test Cases  
Copy and paste directly into LeetCode custom test editor:
```
[1,3,2,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3]
1
[28,5,58,91,24,91,53,9,48,85,16,70,91,91,47,91,61,4,54,61,49]
1
[1,3,2,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3]
2
[3,3,3,3,3]
3
[1,2,3,4,5]
1
[5,5,1,5,2,5,5]
4
[1,1,1,1,1]
5
[10]
1
```
