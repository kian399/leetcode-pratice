Product of Array Except Self
Difficulty: Medium
LeetCode Link: https://leetcode.com/problems/product-of-array-except-self/

Problem Description
Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].
The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.
You must write an algorithm that runs in O(n) time and without using the division operation.

Approach:
1. Brute Force (Not Recommended)
My initial idea was brute force slicing: calculate the product excluding current element for every index.
Time Complexity: O(n²)
Space Complexity: O(n) extra slice memory
This solution has poor time performance and consumes extra memory, so I optimized it.
2. Optimized Two-Pass Solution (Final Implementation)
We split the product into two parts: left cumulative product & right cumulative product.
（1）First left-to-right traverse: store all product values of elements before index i into ans array
（2）Second right-to-left traverse: multiply ans[i] with all product values of elements after index i
Time Complexity: O(n), two single passes
Space Complexity: O(1) extra space (output array does not count as extra space)

Code Implementation:
from typing import List

class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        ans = [1] * n               #Initialize the array so that the ans array has n 1s
        left = 1                    #Caculate left parts，let from left to right that multiply all the numbers 
        for i in range(n):
            ans[i] = left
            left *= nums[i]
        right = 1
        for i in range(n-1, -1, -1):
            ans[i] *= right
            right *= nums[i]
        return ans
        
Reflection & Summary:
     This is a medium-difficulty problem, but it took me a lot of time to optimize.
At first, I tried the brute force slicing approach. However, this method consumes a large amount of memory and performs extremely poorly.
     I redesigned the algorithm to optimize both time and space overhead.
The core idea is to separate the total product into left and right cumulative parts. We only need two full array traversals to get the final result without extra auxiliary arrays.
