- 解法
只要当天的价格高于昨天的价格，就买卖一次，记录总利润
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if len(prices) < 2:
            return 0
        max_prof = 0
        for i in range(1, len(prices)):
            if prices[i]>prices[i-1]:
                max_prof += (prices[i]-prices[i-1])
        return max_prof
```
