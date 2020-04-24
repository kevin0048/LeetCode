- 解法1：二分法
```python
class Solution:
    def mySqrt(self, x: int) -> int:
        def func(left, right, x):
            if left==right-1 and right**2>x:
                return left
            elif right**2==x:
                return right
            
            m = (left+right)//2
            m2 = m**2
            if m2==x:
                return m
            elif m2 > x:
                return func(left, m, x)
            else:
                return func(m, right, x)
        
            
        return func(0,x,x)
```

- 解法2：牛顿法 [wiki](https://en.wikipedia.org/wiki/Integer_square_root#Using_only_integer_division)
```python
class Solution:
    def mySqrt(self, x: int) -> int:
        if x == 0:
            return 0
        
        cur_x = x
        while cur_x > x/cur_x:
            cur_x = (cur_x + x/=cur_x) // 2
            
        return int(cur_x)
```

```python
class Solution:
    def mySqrt(self, x: int) -> int:
        if x == 0:
            return 0
        
        cur_x = x
        while cur_x - x/cur_x > 1e-6:
            cur_x = (cur_x + x/cur_x) / 2
            
        return int(cur_x)
```