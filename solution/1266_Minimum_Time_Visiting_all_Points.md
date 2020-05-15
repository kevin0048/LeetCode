```python
class Solution:
    def minTimeToVisitAllPoints(self, points: List[List[int]]) -> int:
        res = 0
        for i in range(1, len(points)):
            x, y = abs(points[i][0] - points[i-1][0]), abs(points[i][1] - points[i-1][1])
            res = res + min(x,y)+abs(x-y)

        return res
```
