- 解法1
这种解法最简单，遍历两次数组，然后判断子串是不是回文字符串，时间复杂度O(n^3)，
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        def is_pal(s: str) -> bool:
            return s==s[::-1]
        
        if len(s) <= 1:
            return s
        
        max_p = 0
        max_s = None
        for i in range(len(s)):
            for j in range(i, len(s)):
                if is_pal(s[i:j+1]):
                    if max_p < j+1-i:
                        max_p = j+1-i
                        max_s = s[i:j+1]
                        
        return max_s
```
