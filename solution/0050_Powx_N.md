- 解法
快速幂递归解法：
比如求 x^77， x^0->x^1->x^2->x^4->x^9->x^19->x^38->x^77，递归顺序是反过来的，77-38-19-9-4-2-1-0，因为77是奇数，所以它的递归要再乘一个$x(x^38**2 * x)$，同理，19,9,1也是；38是偶数，它的递归项19不用再乘以x

简单来说，类似二分法
1. 计算x^n时，可以先递归地计算出 y=x^(n//2)
2. 根据递归计算的结果，如果n为偶数，x^n=y**2，否则，x^n=y**2*x
3. 递归边界为n=0

由于每次递归都会使得指数减少一半，因此递归的层数为 O(logn)，算法可以在很快的时间内得到结果。
```python
class Solution:
    def myPow(self, x: float, n: int) -> float:
        def quickMul(N):
            if N==0:
                return 1.0
            
            y = quickMul(N//2)
            
            return y * y if N%2 == 0 else y * y * x
        
        return quickMul(n) if n >= 0 else 1.0 / quickMul(-n)
```