```python
class Solution:
    def subtractProductAndSum(self, n: int) -> int:
        n_sum = 0
        n_pro = 1
        while n:
            cur_n = n%10
            n_sum += cur_n
            n_pro*=cur_n

            n//=10

        return n_pro - n_sum
```
