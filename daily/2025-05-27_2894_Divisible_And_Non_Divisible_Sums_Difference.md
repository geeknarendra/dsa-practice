# 2894. Divisible And Non Divisible Sums Difference

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/divisible-and-non-divisible-sums-difference/?envType=daily-question&envId=2025-05-27)


You are given positive integers n and m.

Define two integers as follows:

num1: The sum of all integers in the range [1, n] (both inclusive) that are not divisible by m.
num2: The sum of all integers in the range [1, n] (both inclusive) that are divisible by m.
Return the integer num1 - num2.

## Solution

```python
class Solution:
    def differenceOfSums(self, n: int, m: int) -> int:

        # # Brute force
        # num1,num2=0,0

        # for num in range(1,n+1):
        #     if num%m!=0:
        #         num1+=num
        #     else:
        #         num2+=num
        
        # return num1-num2
        
        # Optimised - Using Maths

        # num1 + num2 = total sum from 1 to n = n*(n+1)/2
        # num1 - num2 = n*(n+1)/2 - 2 * num2
        # Now to calculate num2:
        # numbers divisible by m in range [1,n] form an AP: m, 2m, 3m, ..., km where k = n/m
        # sum of first k terms of AP = k*(2*m+(k-1)m)/2 = k(k+1)*m/2
        
        totalNumSum=n*(n+1)//2

        numOfDivNum=n//m
        sumOfDivNum=(numOfDivNum*(2*m+(numOfDivNum-1)*m))//2
        
        num1=totalNumSum-sumOfDivNum
        num2=sumOfDivNum
        return num1-num2

```


