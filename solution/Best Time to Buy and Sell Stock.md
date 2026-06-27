class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        #初始化最低价格为第一天价格，最大利润
        min_price = prices[0]
        max_profit = 0
        #从第二天开始遍历
        for price in prices[1:]:
            current_profit = price - min_price
        #更新最大利润
            if current_profit > max_profit:
               max_profit = current_profit
        #更新历史最低买入价格
            if price < min_price:
                min_price = price
        return max_profit

commit & push:
