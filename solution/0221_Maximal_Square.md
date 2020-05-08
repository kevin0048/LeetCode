```python

class Solution:
    def maximalSquare(self, matrix: List[List[str]]) -> int:
        max_area = 0
        h = len(matrix)
        if h>0:
            w = len(matrix[0])
        else:
            return 0

        def func(i,j):

            k = 0
            while i+k<h and j+k<w:
                for i1 in range(i,i+k+1):
                    for j1 in range(j,j+k+1):
                        if matrix[i1][j1] =="0":
                            return k*k 
                k += 1
            return k*k

        for i in range(h):
            for j in range(w):
                max_area = max(max_area, func(i,j))

        return max_area
```