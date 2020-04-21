# [整数反转](https://leetcode-cn.com/problems/reverse-integer/)
- 解法1
这个解法还是比较简单的，重点是要判断是正数还是负数，负数的话记录flag
```python
class Solution:
    def reverse(self, x: int) -> int:
        pos = 1 if x >= 0 else 0
        x = x if pos else -x
        
        result = 0
        while x:
            result = result * 10 + x%10
            x //= 10
            
        result = result if pos else -result

        if result<-2**31 or result > 2**31-1:
            return 0
        else:
            return result
```
