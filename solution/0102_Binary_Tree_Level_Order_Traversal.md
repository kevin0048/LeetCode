```python

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        res = {}
        def func(p, depth):
            if p:
                if depth in res:
                    res[depth].append(p.val)
                else:
                    res[depth] = [p.val]
                func(p.left, depth+1)
                func(p.right, depth+1)
        
        func(root, 0)
        ret = []
        for i in range(len(res)):
            ret.append(res[i])

        return ret

```
