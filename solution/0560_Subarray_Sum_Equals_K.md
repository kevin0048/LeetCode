```python
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        count = 0
        mp = {0:1}
        pre = 0
        for i in nums:
            pre += i
            if pre - k in mp:
                count += mp[pre-k]
                
            if pre in mp:
                mp[pre] += 1
            else:
                mp[pre] = 1
                
        return count
```
