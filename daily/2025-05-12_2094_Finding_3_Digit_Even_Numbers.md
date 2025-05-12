# 2094. Finding 3 Digit Even Numbers

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/finding-3-digit-even-numbers/description/?envType=daily-question&envId=2025-05-12)

## Solution

```python
class Solution:
    def findEvenNumbers(self, digits: List[int]) -> List[int]:
        
        res=[]

        digit_cnt=[0]*10
        for digit in digits:
            digit_cnt[digit]+=1

        
        for i in range(1,10):
            digit_cnt[i]-=1
            for j in range(10):
                digit_cnt[j]-=1  
                for k in range(0,10,2):
                    digit_cnt[k]-=1
                    if digit_cnt[i]>=0 and digit_cnt[j]>=0 and digit_cnt[k]>=0:    
                        currNum=100*i+10*j+k
                        res.append(currNum)
                    digit_cnt[k]+=1
                
                digit_cnt[j]+=1   
            digit_cnt[i]+=1

        return res
```

