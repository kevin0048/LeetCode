```python
class Solution:
    def titleToNumber(self, s: str) -> int:
        res = 0
        n = len(s)
        for i in range(n):
            res += (ord(s[i])-64) * 26**(n-i-1)
        return res
```