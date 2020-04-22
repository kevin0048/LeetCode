```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        if needle=="":
            return 0
        elif len(needle) > len(haystack):
            return -1
        else:
            for i in range(len(haystack) - len(needle) + 1):
                if haystack[i:i+len(needle)]==needle:
                    return i
        return -1
```