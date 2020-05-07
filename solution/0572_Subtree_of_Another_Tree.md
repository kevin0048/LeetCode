- 解法
使用递归来求解

1. 首先写一个equal函数来判断两棵树是否相等（结构相等、数值相等）
2. 递归地调用equal对s和t、s.left和t、s.right和t，判断s中是否存在子树和t相等

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isSubtree(self, s: TreeNode, t: TreeNode) -> bool:
        def equal(s, t):
            if not s and not t:
                return True
            elif s and t:
                if s.val != t.val:
                    return False
                else:
                    return equal(s.left, t.left) and equal(s.right, t.right)
            else:
                return False 

        if equal(s, t):
            return True
        else:
            return (s.left and self.isSubtree(s.left, t)) or (s.right and self.isSubtree(s.right, t))
```