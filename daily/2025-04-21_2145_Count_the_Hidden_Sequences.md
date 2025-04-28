# 2145. Count the Hidden Sequences

## Problem Statement
[LeetCode Problem](https://leetcode.com/problems/count-the-hidden-sequences/description/)

Given a list of `differences` and two integers `lower` and `upper`, you need to find the number of valid hidden sequences that can be formed based on the differences. The hidden sequence is formed by starting from some integer `x` and then adding the differences successively. The sequence must be within the range `[lower, upper]`.

## Solution

```python
class Solution:
    def numberOfArrays(self, differences: List[int], lower: int, upper: int) -> int:
        
        # Mathematical Approach 
        # In this approach, we calculate the minimum and maximum values that the hidden sequence can take
        # based on the cumulative sum of the differences and the bounds (lower and upper).
        #
        # We find the range of the hidden sequence by:
        # - Adding the difference to the current sum
        # - Keeping track of the minimum and maximum values encountered
        # The hidden sequence is valid if we start at some integer and it stays within the bounds [lower, upper].
        #
        # For the hidden sequence to be valid:
        # - Max value (from the differences array) + x <= upper --> x <= upper - Max
        # - Min value (from the differences array) + x >= lower --> x >= lower - Min
        #
        # Thus, the valid range for starting x is [lower - Min, upper - Max], 
        # and the number of valid starting points is the size of this range.
	# So the posible count are (UpperRange -LowerRange+1) == (upper-Max-lower+Min+1)
        
        n = len(differences)
        currSum = 0
        rangeMin = rangeMax = 0
        
        # Loop to find the minimum and maximum values in the hidden sequence
        for num in differences:
            currSum += num
            rangeMin = min(rangeMin, currSum)
            rangeMax = max(rangeMax, currSum)
        
        # Return the valid count of hidden sequences that can fit within the range
        return max(0, upper - lower - rangeMax + rangeMin + 1)
        
        # Binary Search Approach
        # In this approach, we use binary search to find the lower and upper bounds for possible starting values.
        # We simulate the sequence generation using the differences array and check if the sequence stays within
        # the bounds [lower, upper] at each step.
        
        n = len(differences)
        
        # Helper function to check if a sequence starting from 'num' stays within the bounds
        def isPossible(num):
            for i in range(n):
                num += differences[i]
                if num < lower:  # If the number goes below the lower bound
                    return -1
                elif num > upper:  # If the number goes above the upper bound
                    return 1
            return 0  # If the sequence stays within bounds
        
        # Function to find the lower bound using binary search
        def lowerBound():
            l, r = lower, upper
            while l <= r:
                mid = (l + r) // 2
                check = isPossible(mid)
                if check >= 0:  # If the sequence is possible, try a smaller number
                    r = mid - 1
                else:
                    l = mid + 1
            return l
        
        # Function to find the upper bound using binary search
        def upperBound():
            l, r = lower, upper
            while l <= r:
                mid = (l + r) // 2
                check = isPossible(mid)
                if check <= 0:  # If the sequence is possible, try a larger number
                    l = mid + 1
                else:
                    r = mid - 1
            return l
        
        # Calculate the valid range for possible starting values
        lB = lowerBound()
        uB = upperBound()
        
        return uB - lB  # Return the number of valid starting points

```

## Additional Test Cases  
Copy and paste directly into LeetCode custom test editor:

```
[2, -2, 3, -3, 4, -4, 5, -5]
0
10
[1, -1, 2, -2, 3, -3, 4, -4, 5, -5]
-3
7
[3, -2, 1, -3, 2, -1, 3, -3]
1
8
[1, 1, 1, 1, 1, -5]
0
5
[5, -4, 3, -2, 1, -1, -2, 2, -3, 3]
-2
6
[1, 2, -1, -2, 3, -3, 4, -4, 5, -5]
0
10
[4, -4, 4, -4, 4, -4, 4, -4, 4]
-5
5
[-40]
-46
53
```

