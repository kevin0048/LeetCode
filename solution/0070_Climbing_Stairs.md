- 解法1：不能AC，超时
递归大法
```python

class Solution:
    def climbStairs(self, n: int) -> int:
        if n<=2:
            return n
        else:
            return self.climbStairs(n-1) + self.climbStairs(n-2)
```

- 解法2：
 第i步的结果都是第i-1步+第i-2步的结果加起来的，这样一直加到n就行了
 
```
class Solution:
    def climbStairs(self, n: int) -> int:
        if n<=2:
            return n
        i1,i2 = 1,2
        for i in range(3,n+1):
            tmp = i1+i2
            i1 = i2
            i2 = tmp
        return tmp
```
