- 解法1
使用一个字典存储每一层的数字，递归遍历每一颗子树
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def levelOrderBottom(self, root: TreeNode) -> List[List[int]]:
        if root is None:
            return []
        res = {}
        def func(r, depth):
            if r is not None:
                if depth in res:
                    res[depth].append(r.val)
                else:
                    res[depth] = [r.val]
                func(r.left, depth+1)
                func(r.right, depth+1)
            else:
                return
        func(root, 0)

        ret = []
        i = 0
        while 1:
            if i in res:
                ret.append(res[i])
                i += 1
            else:
                return ret[::-1]

        
```

- 解法2
不用字典存，直接用数组存，居然内存消耗差不多。。。
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def levelOrderBottom(self, root: TreeNode) -> List[List[int]]:
        if root is None:
            return []
        res = []
        def func(r, depth):
            if r is not None:
                if len(res) > depth:
                    res[depth].append(r.val)
                else:
                    res.append([r.val])
                func(r.left, depth+1)
                func(r.right, depth+1)
            else:
                return
        func(root, 0)

        return res[::-1]
```
