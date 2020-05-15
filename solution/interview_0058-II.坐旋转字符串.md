```python
class Solution:
    def reverseLeftWords(self, s: str, n: int) -> str:
        len_n = len(s)
        n %= len_n

        return s[n:]+s[:n]
```
