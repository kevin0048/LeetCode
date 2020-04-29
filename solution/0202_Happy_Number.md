使用一个list存放计算过的n，如果n在list中，返回False，如果n=1，返回True

```python
class Solution:
    def isHappy(self, n: int) -> bool:
        ret = []
        while 1:
            tmp = 0
            while n:
                tmp += (n%10)**2
                n //= 10
            if tmp==1:
                return True
            if tmp in ret:
                return False
            else:
                ret.append(tmp)
            n = tmp
```