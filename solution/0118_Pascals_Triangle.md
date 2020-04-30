```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        if numRows==0:
            return []
        res = [[1]]
        for i in range(1, numRows):
            tmp = res[i-1]
            cur = [1]
            for i in range(1,len(tmp)):
                cur.append(tmp[i-1]+tmp[i])
            cur.append(1)
            res.append(cur)
        return res
```

错位相加法
```python
class Solution:
    def generate(self, numRows: int):
        if numRows==0:
            return []
        
        res = [[1]]
        while len(res) < numRows:
            res.append([i+j for i,j in zip([0]+res[-1], res[-1]+[0])])
        return res
```
