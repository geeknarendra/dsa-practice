# 2799. Count Complete Subarrays in an Array

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/count-complete-subarrays-in-an-array/description/)

You are given an array nums consisting of positive integers.

We call a subarray of an array complete if the following condition is satisfied:

The number of distinct elements in the subarray is equal to the number of distinct elements in the whole array.
Return the number of complete subarrays.

A subarray is a contiguous non-empty part of an array.

## Solution

```python
class Solution:
    def countCompleteSubarrays(self, nums: List[int]) -> int:
        n=len(nums)
        res=0
        distintEleCnt=len(set(nums))

        seenFreq=defaultdict(int)
        
        i=j=0
        while j<n:
            seenFreq[nums[j]]+=1

            while len(seenFreq)==distintEleCnt and i<=j:
                res+=(n-j)
                # print(i,n-j)
                seenFreq[nums[i]]-=1

                if seenFreq[nums[i]]==0:
                    del seenFreq[nums[i]]
                i+=1

            j+=1
        
        return res
       
```


## Additional Test Cases  
Copy and paste directly into LeetCode custom test editor:

```
[42]
[1,2,3,4,5]
[1,2,3,1,2,4,5,6]
[5,4,3,2,1,5,4,3,2,1]
[1,2,3,4,5,1,2,3,4,5]
[1,1,1,2,2,2,3,3,3,4,4,4]
[10,9,8,7,6,5,4,3,2,1]
[1,2,1,3,1,4,1,5,1]
[1,1,2,2,3,3,4,4,5]
[999,1000,999,1000,999]
[1,2,3,2,1]
[3,1,2,3,4,5,6,5,4,3,2,1]
```