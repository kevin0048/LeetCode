根据规则设定一些if else就行了


```python
class Solution:
    def myAtoi(self, str: str) -> int:
        result = 0
        # 剔除前导空格
        while len(str):
            if str[0]==" ":
                str = str[1:]
            else:
                break     
        if len(str)==0:
            return 0
        sign = 1
        if str[0]=="+":
            sign = 1
            str = str[1:]
        elif str[0]=="-":
            sign = -1
            str = str[1:]
        while str:
            if ord(str[0]) >= ord("0") and ord(str[0]) <= ord("9"):
                result = result * 10 + int(str[0])
                str = str[1:]
            else:
                break
        
        result *= sign
        if result > 2**31-1:
            return 2**31-1
        elif result < -2**31:
            return -2**31
        else:
            return result
            
```