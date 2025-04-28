# 1399. Count Largest Group

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/count-largest-group/description/)

You are given an integer n.

We need to group the numbers from 1 to n according to the sum of its digits. For example, the numbers 14 and 5 belong to the same group, whereas 13 and 3 belong to different groups.

Return the number of groups that have the largest size, i.e. the maximum number of elements.

## Solution

```python
class Solution:

    def digitSum(self,num):
        currSum=0
        while num>0:
            currSum+=num%10
            num//=10
        return currSum

    def countLargestGroup(self, n: int) -> int:


#------------------------------------------------------------------------#

# Approach 2: Using Array for sum range
# Complexity -> Time complexity will be O(n * log n) ,  because for each number up to n, we compute the digit sum in O(log n) time.
                #  Space -O(1)

        cntOfGroup=0
        largestSize=0

        # As range is 1<10*4 --> 1 to 9999 =>Sum range [1,36]

        sumFreq=[0]*(36+1)
        for num in range(1,n+1):
            currSum=self.digitSum(num)
            sumFreq[currSum]+=1
            largestSize=max(largestSize,sumFreq[currSum])
        
        for currSum in range(1,36+1):
            if sumFreq[currSum]==largestSize:
                cntOfGroup+=1
                
        return cntOfGroup

#------------------------------------------------------------------------#

# # Approach 1: Using HashMap
# # Complexity -> Time complexity will be O(n * log n) ,  because for each number up to n, we compute the digit sum in O(log n) time.
##                Space -O(N) - Space for HashMap

#         cntOfGroup=0
#         largestSize=0
#         # Using HashMap
#         sumFreq=defaultdict(int)

#         for num in range(1,n+1):
#             currSum=currSum=self.digitSum(num)
            
#             sumFreq[currSum]+=1
#             largestSize=max(largestSize,sumFreq[currSum])

#         for cnt in sumFreq.values():
#             if cnt==largestSize:
#                 cntOfGroup+=1
#         return cntOfGroup
    
       
```


## Additional Test Cases  
Copy and paste directly into LeetCode custom test editor:

```
8
44
80
929
29
92
3680
10000
```