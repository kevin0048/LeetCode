- 解法1
遍历字符串
```
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        last_len = 0
        world_flag = False # 是否已开始单词
        begin = 0 # 单词开始index

        for i in range(len(s)):
            if ord(s[i]) == ord(' '):# 该字符是空格
                if world_flag:
                    last_len = i-begin
                    world_flag = False

            else: # 该字符不是空格
                if not world_flag: #如果没有开始单词，则单词开始；如果开始了单词，pass
                    world_flag = True
                    begin = i
                    
                    if i==len(s)-1: # 如果最后只有一个字符
                        last_len = 1
                else: #如果开始了单词，且该字符也是字母，且到了最后一个字符
                    if i==len(s)-1:
                        last_len = i - begin + 1
                    
        return last_len
```

- 解法2：
抖机灵
```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        s = s.strip(" ")
        return 0 if len(s)==0 else len(s.split(" ")[-1])
```
