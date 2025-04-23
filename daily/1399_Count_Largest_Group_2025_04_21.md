# 1399. Count Largest Group

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/count-largest-group/description/)

- You are given an integer n.
- Each number from 1 to n is grouped according to the sum of its digits.
- Return the number of groups that have the largest size.


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
99
29
38
39
991
9999
1000
5566
```