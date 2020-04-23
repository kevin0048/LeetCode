```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        i = len(a) - 1
        j = len(b) - 1
        res = ""
        bit = 0
        
        while i>=0 and j>=0:
            cur_bit = int(a[i]) + int(b[j]) + bit
            bit = 0
            if cur_bit > 1:
                bit = 1
                cur_bit -= 2

            res = str(cur_bit) + res
                
            i -= 1
            j -= 1
        
        while i>=0:
            cur_bit = int(a[i]) + bit
            bit = 0
            if cur_bit > 1:
                bit = 1
                cur_bit -= 2
    
            res = str(cur_bit) + res
            i -= 1
            
        while j>=0:
            cur_bit = int(b[j]) + bit
            bit = 0
            if cur_bit > 1:
                bit = 1
                cur_bit -= 2

            res = str(cur_bit) + res
            j -= 1
            
        if bit:
            res = "1" + res
            
        return res
```
