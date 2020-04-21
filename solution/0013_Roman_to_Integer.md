```python
class Solution:
    def romanToInt(self, s: str) -> int:
        roman_map = {
            "I":1,
            "V":5,
            "X":10,
            "L":50,
            "C":100,
            "D":500,
            "M":1000,
            "IV":4,
            "IX":9,
            "XL":40,
            "XC":90,
            "CD":400,
            "CM":900
        }
            
        result, i = 0, 0
        len_s = len(s)
        while i < len_s:
            if i+1< len_s:
                if roman_map.get(s[i:i+2]):
                    result += roman_map.get(s[i:i+2])
                    i += 2
                else:
                    result += roman_map.get(s[i])
                    i += 1
            else:
                result += roman_map.get(s[i])
                i += 1
        return result
```
