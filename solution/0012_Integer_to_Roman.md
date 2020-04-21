```python
class Solution:
    def intToRoman(self, num: int) -> str:
        
        roman_map = {
            1:"I",
            5:"V",
            10:"X",
            50:"L",
            100:"C",
            500:"D",
            1000:"M",
            4:"IV",
            9:"IX",
            40:"XL",
            90:"XC",
            400:"CD",
            900:"CM"
        }
        result = ""
        
        e = 0
        while num:
            cur_bit = num % 10
            if cur_bit==4 or cur_bit== 9:
                result = roman_map.get(cur_bit*10**e) + result
            
            elif cur_bit < 4:
                result = roman_map.get(1*10**e)*cur_bit + result
            else:
                result = roman_map.get(5*10**e) + roman_map.get(1*10**e)*(cur_bit-5) + result
            
            num //= 10
            e += 1

        return result
```
