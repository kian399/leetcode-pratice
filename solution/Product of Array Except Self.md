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
        
