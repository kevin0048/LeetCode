- 解法1
前面有一道题是nums中只有两个数字不一样

如果两个数字一样，异或结果为0；那么对nums中的所有数字进行异或，得到的就是那个单独的数字

```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        return functools.reduce(lambda x,y:x^y, nums)
```