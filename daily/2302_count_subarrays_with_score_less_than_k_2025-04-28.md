# 2302. Count Subarrays With Score Less Than K

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/count-subarrays-with-score-less-than-k/description/?envType=daily-question&envId=2025-04-28)

The score of an array is defined as the product of its sum and its length.

For example, the score of [1, 2, 3, 4, 5] is (1 + 2 + 3 + 4 + 5) * 5 = 75.
Given a positive integer array nums and an integer k, return the number of non-empty subarrays of nums whose score is strictly less than k.

A subarray is a contiguous sequence of elements within an array.

## Solution

```python
class Solution:
    def countSubarrays(self, nums: List[int], k: int) -> int:
        n=len(nums)
        res=0
        left=0
        currSum=0

        for right in range(n):
            currSum+=nums[right]


            while currSum*(right-left+1)>=k:
                currSum-=nums[left]
                left+=1
                
            if currSum*(right-left+1)<k:
                res+=(right-left+1)            
        

        return res
```

## Additional Test Cases  
Copy and paste directly into LeetCode custom test editor:

```
[1]
1
[1]
2
[2, 16, 14, 16, 11, 13, 15, 16, 6, 10]
50
[11, 28, 4, 40, 17, 27, 2, 2, 16, 32]
5
[3228, 69040, 78987, 91272, 30479, 24963, 46345, 9764, 35471, 85790, 99941, 38661, 82580, 73375, 22447, 25039, 25921, 58146, 14074, 63926]
1000000
[2, 1, 1, 1, 1, 1, 1, 1, 2, 2, 2, 1, 2, 2, 2, 2, 2, 1, 2, 1, 2, 1, 2, 2, 1, 1, 2, 1, 1, 2, 1, 1, 1, 1, 2, 1, 1, 2, 1, 2, 1, 2, 1, 1, 1, 1, 1, 2, 2, 2, 1, 1, 1, 1, 2, 1, 2, 1, 1, 1, 2, 1, 1, 2, 1, 2, 2, 2, 2, 2, 1, 1, 1, 2, 2, 1, 2, 2, 1, 2, 2, 2, 1, 1, 1, 1, 1, 2, 1, 2, 1, 2, 1, 1, 2, 1, 1, 2, 2, 1]
100
[1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
10001
```


