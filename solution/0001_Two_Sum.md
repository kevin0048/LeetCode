# 1. [两数之和](https://leetcode-cn.com/problems/two-sum/)

- 20200420
遍历两次数组，应该可以得到一个基础的解法，但是时间和空间复杂度不是最佳
```python3
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i,j]
```

eee，发现在[国外社区](https://leetcode.com/problems/two-sum)可以AC（虽然Runtime很长），在[国内社区](https://leetcode-cn.com/problems/two-sum/)就显示超时，还是有待优化