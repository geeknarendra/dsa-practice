# 3335. Total Characters In String After Transformations I

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/total-characters-in-string-after-transformations-i/description/?envType=daily-question&envId=2025-05-13)
You are given a string s and an integer t, representing the number of transformations to perform. In one transformation, every character in s is replaced according to the following rules:

If the character is 'z', replace it with the string "ab".
Otherwise, replace it with the next character in the alphabet. For example, 'a' is replaced with 'b', 'b' is replaced with 'c', and so on.
Return the length of the resulting string after exactly t transformations.

Since the answer may be very large, return it modulo 109 + 7.


## Solution

```python
class Solution:
    def lengthAfterTransformations(self, s: str, t: int) -> int:
        MOD=10**9+7

        res=0
        chr_array=[0]*26
        for chr in s:
            
            chr_array[ord(chr)-ord('a')]+=1

        # print(chr_array)
        for _ in range(t):
            
            lst=chr_array[0]
            chr_array[0]=0
            for i in range(1,26):
                if i==25:
                    chr_array[0]+=chr_array[i]
                    chr_array[1]+=chr_array[i]
                
                lst,chr_array[i]=chr_array[i],lst

        # print(chr_array)
        
        for i in range(26):
            res=(res+(chr_array[i]%MOD))%MOD
        
        return res
        
```
## Complexity 
```
Time - O(N+T)
Space - O(26)--> O(1)
```
## Additional Test Cases  
Copy and paste directly into LeetCode custom test editor:
```
"abcyy"
2
"azbk"
1
"abbcccyyz"
27
"axyz"
27
"jqktcurgdvlibczdsvnsg"
7517
```
