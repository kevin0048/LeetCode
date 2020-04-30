- 解法1
迭代上次的结果
```python
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:        
        i = 0
        res = [1]
        while i < rowIndex:
            res=([i+j for i,j in zip([0]+res, res+[0])])
            i += 1
        return res
```

- 解法2
直接申请一个那么长的数组，每次修改数组中不同位置的值
```python
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:        
        res = [1]*(rowIndex+1)
        if rowIndex<2:
            return res
        
        for i in range(rowIndex+1):
            j = i-1
            while j>0:
                res[j] = res[j]+res[j-1]
                j-=1
        return res
```
