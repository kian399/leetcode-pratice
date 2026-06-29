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
        
commit & push:
Although it is a midle diffciultly question that still spend me lots of times.At first,I tend to use Violent slicing method,however,I found that require a large amoumt of memory space and perform extermely poorly.Consequnently,I optimized my algorithm, not only in terms of time but also space. Each value in the nums array is multiplied by 1 and then cumulatively multiplied into the ans array, obtaining left and right parts. The concept is similar, but the new method only requires traversing twice.                                   
