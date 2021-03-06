---
layout: post
title: "171. Excel Sheet Column Number"
tag: leetcode刷题笔记
---

Given a column title as appear in an Excel sheet, return its corresponding column number.

**For example:**

    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...

**Example 1:**

Input: "A"

Output: 1

**Example 2:**

Input: "AB"

Output: 28

**Example 3:**

Input: "ZY"

Output: 701

**思路：**
以26为周期
先看输入字符串的长度
其实就是26进制转化为10进制的思想（参考网上<https://blog.csdn.net/NXHYD/article/details/71713837>）
~~~
class Solution(object):
    def titleToNumber(self, s):
        """
        :type s: str
        :rtype: int
        """
        Sum = 0
        length = len(s)
        if length == 0:
            return 0
        for i in range(0, length):
            # print(i)
            # print(length-i-1)
            Sum += pow(26, length-i-1) * (ord(s[i])-64)
        return Sum

if __name__ == "__main__":
    c = "AB"
    print(Solution().titleToNumber(c))
~~~    

**注：**
>ord（）函数就是用来返回单个字符的ascii值（0-255）或者unicode数值
采用ord()-64可以得到相应整数
pow函数的使用
