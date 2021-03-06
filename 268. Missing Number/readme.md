Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

**Example 1:**

Input: [3,0,1]
Output: 2
**Example 2:**

Input: [9,6,4,2,3,5,7,0,1]
Output: 8
Note:
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?
给定一个包含n个不同数字的数组，取自0,1,2，...，n，找到数组中缺少的数字。

注意：
您的算法应该以线性运行时复杂性运行。 你能用恒定的额外空间复杂度来实现吗？

**思路：**
恒定的额外空间复杂度怎么搞？
蛮力法
二分法，每次只比较一半
先对原数组进行排序
**注意点：**
原先的数组可能也已经是已经拍好序的了
~~~
class Solution(object):
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        nums.sort()
        min = nums[0]
        max = nums[len(nums)-1]
        if len(nums) == max-min+1:
            if min == 0:
                return max+1
            else:
                return 0
        #print(min)-0
        #print(max)-1
        j = 0
        for i in range(min, max+1):
            if nums[j] != i:
                return i
            else:
                j += 1
~~~
**网上例子：**
<https://blog.csdn.net/u014251967/article/details/52473505>
按题目要求的正确的应该是从0开始！！
所以直接比较
~~~
 nums.sort()
        i = 0
        while i < len(nums):
            if nums[i] != i :
                return i
            else:
                i += 1
        return i
~~~
>另，等差数列求和
异或（没大看懂）

