```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        dic = {}
        n = len(nums)
        for i in nums:
            if i in dic:
                dic[i] += 1
                if dic[i]>(n>>1):
                    return i
            else:
                dic[i] = 1
        
        for i in dic:
            if dic[i]>(n>>1):
                return i

```
