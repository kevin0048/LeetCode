```python
class Solution:
    def convertToTitle(self, n: int) -> str:
        res = ""
        while n > 0:
            if n%26==0:
                res = "Z" + res
                n = n//26-1
            else:
                res = chr(64+n%26) + res
                n//=26
        return res
```