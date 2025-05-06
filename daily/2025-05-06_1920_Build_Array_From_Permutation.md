# 1920. Build Array From Permutation

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/build-array-from-permutation/description/?envType=daily-question&envId=2025-05-06)

Given a zero-based permutation nums (0-indexed), build an array ans of the same length where ans[i] = nums[nums[i]] for each 0 <= i < nums.length and return it.

A zero-based permutation nums is an array of distinct integers from 0 to nums.length - 1 (inclusive).


## Hint

For Easy : Just use the logic which is asked don`t think more.
For Medium : Not to use extra space, Try to use logic where you save current and result number in the current index.

## Solution

```python
class Solution:
    def buildArray(self, nums: List[int]) -> List[int]:
        
# Time -O(N)
# Space -O(1) -> Used Nums array for result array
        n=len(nums)

        for i in range(n):
            nums[i]=(nums[nums[i]]%n)*n+(nums[i])
        
        # print(nums)
        nums=[num//n for num in nums]

        return nums

##########################################################
# Time O(N)
# Space O(N) - Extra Space for result array

        n=len(nums)
        res=[-1]*n

        for i in range(n):
            res[i]=nums[nums[i]]

        return res
```

## Additional Test Cases  
Copy and paste directly into LeetCode custom test editor:
```
[0]
[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
[41, 9, 57, 56, 13, 39, 44, 97, 37, 58, 62, 99, 82, 78, 30, 6, 77, 65, 27, 53, 73, 94, 20, 74, 11, 1, 93, 80, 79, 12, 76, 5, 40, 55, 59, 2, 64, 23, 43, 22, 16, 18, 86, 67, 66, 33, 81, 49, 42, 51, 0, 31, 88, 36, 69, 38, 24, 14, 60, 85, 3, 98, 75, 34, 32, 96, 28, 46, 47, 35, 17, 84, 8, 61, 21, 7, 4, 90, 48, 10, 54, 92, 83, 70, 52, 26, 71, 89, 29, 95, 25, 45, 68, 19, 72, 91, 50, 63, 15, 87]
```
