```python
class Solution:
    def kidsWithCandies(self, candies: List[int], extraCandies: int) -> List[bool]:
        max_n = max(candies)
        res = [True if i+extraCandies>=max_n else False for i in candies]
        return res
```
