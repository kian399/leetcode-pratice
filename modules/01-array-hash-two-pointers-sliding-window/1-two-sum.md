# 1. Two Sum
## 题目
给定一个整数数组 nums 和一个整数目标值 target，在数组中找出和为 target 的两个整数，返回它们的下标。
## 思路
哈希表存「值→下标」，遍历一次：对每个数 num，检查 target-num 是否在哈希表里，在就直接返回，不在就把当前数存进去。
## 代码
 `python
def twoSum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        if target - num in seen:
            return [seen[target - num], i]
        seen[num] = i
 `
## 复杂度
时间 O(n)，空间 O(n)
