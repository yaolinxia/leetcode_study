---
layout: post
title: "198. House Robber"
tag: leetcode刷题笔记
---

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.
每个房子都有一定数量的金钱藏匿，唯一的限制就是停止抢劫他们每个房屋是相邻的房屋有连接的安全系统，如果两个相邻的房子在同一个晚上被打破，它将自动联系警察。

给出一个代表每个房子的金额的非负整数列表，确定今晚可以抢劫的最大金额而不警告警察。

**Example 1:**
Input: [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
             Total amount you can rob = 1 + 3 = 4.
输入：[1,2,3,1]
输出：4
说明：Rob house 1（money = 1）然后抢房子3（钱= 3）。
您可以抢夺的总金额= 1 + 3 = 4。
             
**Example 2:**
Input: [2,7,9,3,1]
Output: 12
Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
             Total amount you can rob = 2 + 9 + 1 = 12.
输入：[2,7,9,3,1]
产量：12
说明：Rob house 1（money = 2），rob house 3（money = 9）和rob house 5（money = 1）。
您可以抢夺的总金额= 2 + 9 + 1 = 12。

**思路:**
遍历列表；
从第一个以及第二个开始，都是间隔一个开始遍历
直到遍历完列表中所有元素
>该思路有问题

**网上思路：**
<https://blog.csdn.net/coder_orz/article/details/51555813>
典型动态规划的问题

~~~
class Solution(object):
    def rob(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if len(nums) == 0:
            return 0
        elif len(nums) < 2:
            return max(nums[0], nums[-1])
        #进行记录，为一个列表，初始化，所有元素均为0
        money = [0]*len(nums)
        money[0], money[1] = nums[0], max(nums[0], nums[1])
        for i in range(2, len(nums)):
            money[i] = max(nums[i] + money[i-2], money[i-1])
        return money[len(nums)-1]

if __name__ == "__main__":
    nums = [2, 7, 9, 3, 1]
    print(Solution().rob(nums))
~~~
    