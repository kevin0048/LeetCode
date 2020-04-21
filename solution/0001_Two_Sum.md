# [两数之和](https://leetcode-cn.com/problems/two-sum/)

- 解法1：暴力法
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i,j]
```

eee，发现在[国外社区](https://leetcode.com/problems/two-sum)可以AC（虽然Runtime很长），在[国内社区](https://leetcode-cn.com/problems/two-sum/)就显示超时，还是有待优化

看了下官方题解，第一种方法就是java的暴力法，可能是python的速度比较慢吧

- 解法2：使用一个额外的dict保存遍历过的数据

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dct = {}
        for i, n in enumerate(nums):
            if target - n in dct:
                return [dct[target - n], i]
            dct[n] = i
```

解法1的时间复杂度$O(n^2)$，解法2的时间复杂度为$O(n)$，因为字典的查找是$O(1)$的，所以不会超时；但是解法2的额外增加了一个空间复杂度为$O(n)$的dict

