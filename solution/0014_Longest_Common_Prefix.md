```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        if len(strs)==0:
            return ""

        longest_index = 0
        
        min_len = min([len(item) for item in strs])
        while longest_index<min_len:
            if len(set([item[longest_index] for item in strs])) == 1:
                longest_index += 1
            else:
                break
            
        return strs[0][:longest_index]
```
