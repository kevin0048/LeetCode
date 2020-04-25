- 解法1：遍历两次数组
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        max_len = 0
        l = len(s)
        if l<2:
            return l
        
        for i in range(l):
            for j in range(i, l):
                if j-i+1 == len(set(list(s[i:j+1]))):
                    max_len = j-i+1 if max_len < j-i+1 else max_len
                else:
                    break
                    
        return max_len
```

- 解法2：
遍历一次数组，使用一个额外的dict来保存每个字符在s中出现的最大index

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        st = {} # 记录每一个字符最新的往后一位的index
        s_i = max_len = 0 # 子串开始的index s_i， 最大长度max_len
        
        for i in range(len(s)):
            if s[i] in st:
                s_i = max(s_i, st[s[i]]) # 更新当前子串开始的index
            max_len = max(max_len, i - s_i + 1) # 更新最大无重复子串
            st[s[i]] = i+1
        return max_len
```