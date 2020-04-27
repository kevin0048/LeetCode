- 解法1
遍历数组，根据规则，将每个字符分到第count行的字符串中，最后将每一行的字符串拼接起来
```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if len(s)==0:
            return s

        res = ['' for _ in range(numRows)]
        count = 0
        i=0

        while i < len(s):
            count = 0
            while count<numRows:
                res[count] = res[count]+s[i]
                count += 1
                i += 1
                if i==len(s):
                    return "".join(res)
                
            count -= 2
            while count >= 1:
                res[count] = res[count]+s[i]
                count -= 1
                i += 1
                if i==len(s):
                    return "".join(res)

```