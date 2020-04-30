- 解法1
与0002类似，使用一个字典来存之前遍历过的数字
```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        if len(numbers) < 2:
            return []
        dic = {}
        for i in range(len(numbers)):
            if target-numbers[i] in dic:
                return [dic[target-numbers[i]]+1, i+1]
            else:
                dic[numbers[i]] = i
        return []
```
