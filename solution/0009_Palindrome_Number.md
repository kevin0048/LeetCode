# [回文数](https://leetcode-cn.com/problems/palindrome-number/)

这道题可以使用[整数反转](0007_Reverse_Integer.md)的方法，对于正整数计算反转，然后判断是否相等

```
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0:
            return False

        inverse_num = 0
        x_num = x
        while x:
            inverse_num = inverse_num * 10 + x%10
            x //= 10

        if x_num == inverse_num:
            return True
        else:
            return False
```
