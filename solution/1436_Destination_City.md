```python
class Solution:
    def destCity(self, paths: List[List[str]]) -> str:
        in_point = []
        out_point = []

        for point in paths:
            in_point.append(point[0])
            out_point.append(point[1])

        for p in out_point:
            if p not in in_point:
                return p
```
