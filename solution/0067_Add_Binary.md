- 解法1
从末尾按位计算，如果位数大于1，则该位减2，且向下一位进位
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


- 解法2
使用按位XOR做加法，按位&进位

首先把a和b转换成整型数字x和y，x保存结果，y保存进位；当进位不为0时：
1. 计算当前x和y的无进位相加结果： answer = x^y
2. 计算当前x和y的进位：carry = (x&y) << 1
3. 完成本次循环，更新： x = answer,y=carry
最后返回x的二进制形式
```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        x, y = int(a, 2), int(b, 2)
        while y:
            x, y = x ^ y, (x&y) << 1
            
        return bin(x)[2:]

```
