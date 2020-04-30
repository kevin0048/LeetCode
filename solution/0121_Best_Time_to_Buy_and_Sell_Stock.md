- 解法
1. 初始化当日往前最低值 min_p， 最大利润max_prof=0
2. 遍历数组[1:]，如果当天价格低于min_p，替换min_p为当日价格；如果当日卖出（减去min_p）的利润大于max_prof，替换max_prof

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if len(prices)<2:
            return 0
        min_p = prices[0]
        max_prof = 0
        
        for i in range(1, len(prices)):
            if prices[i] < min_p:
                min_p = prices[i]
            max_prof = prices[i] - min_p if prices[i]-min_p>max_prof else max_prof
            
        return max_prof
```