```python
class Solution:
    def smallerNumbersThanCurrent(self, nums: List[int]) -> List[int]:
        res = []
        for i in nums:
            res.append(sum([1 if j<i else 0 for j in nums]))

        return res
```
