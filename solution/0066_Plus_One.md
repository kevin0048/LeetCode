- 解法1
```python

class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        n = len(digits)
        digits[n-1] += 1
        
        # 进位
        bit = 0
        i = n-1
        while i>=0:
            if bit + digits[i]==10:
                if i==0:
                    digits[i]=0
                    return [1]+digits
                else:
                    digits[i]=0
                    bit = 1
            else:
                digits[i] = bit + digits[i]
                return digits
            
            i -= 1
        
        return digits
```

- 解法2
抖机灵
```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        return [int(i) for i in list(str(int("".join(map(str, digits)))+1))]
```
