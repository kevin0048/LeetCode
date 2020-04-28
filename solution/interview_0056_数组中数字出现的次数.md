- 解法1
题目要求时间复杂度O(n)，空间复杂度O(1)，说明只能用一些奇奇怪怪的方法解决。
这个解法可以AC，但是时间复杂度不符合要求。
```python
class Solution:
    def singleNumbers(self, nums: List[int]) -> List[int]:
        res = []
        for i in range(len(nums)):
            if nums[i] in nums[:i] or nums[i] in nums[i+1:]:
                pass
            else:
                res.append(nums[i])
        return res
```

- 解法2
官方解法，假设不同数字为a,b
1. 首先全部数字进行异或，数字相同的异或为0，所以全部数字异或的结果等于a和b异或的结果；异或结果为x
2. 取x最低位为1的位数x0，作为对输入分组的根据：如果两个数字相等，那么这两个数字在x0位上的二进制值一样；打个比方，把x0位上等于0的分为A组，x0位上等于1的分为B组；这样，数字a和b被分别分到了不同的组，而且其他数字相同的也分到了同一组
3. 分别对A组和B组进行异或，得到结果
```python
class Solution:
    def singleNumbers(self, nums: List[int]) -> List[int]:
        ret = functools.reduce(lambda x,y: x^y, nums)
        div = 1
        while ret & div == 0:
            div <<= 1

        a, b = 0, 0
        for n in  nums:
            if n & div:
                a ^= n
            else:
                b ^= n

        return [a,b]
```
