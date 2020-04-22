- 解法1:
思路简单，因为结果跟标准的顺序不一样，所以不能AC

整体思路，先生成一对括号"()"
    对上一步的结果遍历，分成3种情况，1：扩住上一个结果"(())"，2：在左边加一个括号"()()"，3：在右边加一个括号"()()"，然后判断2和3是不是重复的，如果不是重复的，把三个加到新的结果中，如果是，只加两个

```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        if n==0:
            return []
        elif n==1:
            return ["()"]
        else:
            result = ["()"]
            for i in range(1,n):
                tmp_result = []
                for item in result:
                    m = "("+item+")"
                    l = "()"+item
                    r = item+"()"
                    if l==r:
                        tmp_result.append(m)
                        tmp_result.append(l)
                    else:
                        tmp_result.append(m)
                        tmp_result.append(l)
                        tmp_result.append(r)
                result = tmp_result
        return sorted(result)
```

解法2：DFS
添加结果条件：l=r=n
左遍历条件：l<n
右遍历条件：r<l
```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        result = []
        def func(l, r, s):
            if l==r==n:
                result.append(s)
            if l<n:
                func(l+1, r, s+'(')
            if r<l:
                func(l, r+1, s+')')
        func(0,0,'')
        return result
```

