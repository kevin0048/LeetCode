- 解法1：
从s的头部和尾部同时遍历s，每遍历到一个符合条件（数字或字母）的字符串，判断头部和尾部的是否相等；要注意start和end的临界点

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        start = 0
        end = len(s) - 1
        while start<end:
            while start<=end:
                if (s[start].lower() >= 'a' and  s[start].lower() <= 'z') or (s[start]>='0' and s[start]<='9'):
                    break
                else:
                    start += 1

            if start > end:
                return True

            while start<=end:
                if (s[end].lower() >= 'a' and s[end].lower() <= 'z') or (s[end]>='0' and s[end]<='9'):
                    break
                else:
                    end -= 1
            if start > end:
                return True

            if s[start].lower() != s[end].lower():
                return False
            
            else:
                start += 1
                end -= 1
                
        return True
```