- 贪心算法
遍历数组，并且在每个步骤中更新：
1. 当前元素 i
2. 当前元素位置的最大和 cur\_sum
3. 迄今为止最大和 res


```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        res = nums[0]
        cur_sum = 0
        
        for i in nums:
            if cur_sum > 0:
                cur_sum += i
            else:
                cur_sum = i
            res = max(res, cur_sum)
        return res
```
