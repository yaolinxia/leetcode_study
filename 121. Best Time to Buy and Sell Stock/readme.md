Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Note that you cannot sell a stock before you buy one.
假设您有一个数组，其中第i个元素是第i天给定股票的价格。

如果您只被允许完成最多一笔交易（即买入并卖出一股股票），请设计算法以找到最大利润。

请注意，在购买之前不能出售股票。

**Example 1:**

Input: [7,1,5,3,6,4]

Output: 5

**Explanation:** Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
             Not 7-1 = 6, as selling price needs to be larger than buying price.
说明：在第2天买入（价格= 1）并在第5天卖出（价格= 6），利润= 6-1 = 5。
              不是7-1 = 6，因为售价需要大于购买价格。

**Example 2:**

Input: [7,6,4,3,1]
Output: 0

**Explanation:** In this case, no transaction is done, i.e. max profit = 0.

说明：在这种情况下，不进行任何交易，即最大利润= 0。

**思路：**
- 售价需要大于购买价格
- 就是顺向寻找列表中元素相互之间的最大差值。这个就是理论
- 蛮力法，依次遍历
~~~
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """

        maxP = 0
        for i in range(0, len(prices)):
            for j in range(i+1, len(prices)):
                if prices[j] > prices[i]:
                    if prices[j] - prices[i] > maxP:
                        maxP = prices[j] - prices[i]
        return maxP

if __name__ == "__main__":
    pic = [7,6,4,3,1]
    pic0 = Solution().maxProfit(pic)
    print(pic0)
~~~
**运行结果：**
>提交时，显示超时。

>采纳网上思路，只需要遍历一遍。
<https://blog.csdn.net/coder_orz/article/details/51520971>

~~~
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        if len(prices) == 0:
            return 0
        maxP = 0
        minS = prices[0]
        for i in range(1, len(prices)):
            if prices[i] < minS:
                minS = prices[i]
            elif prices[i] - minS > maxP:
                maxP = prices[i] - minS

        return maxP

if __name__ == "__main__":
    pic = [7,1,5,3,6,4]
    pic0 = Solution().maxProfit(pic)
    print(pic0)
~~~
