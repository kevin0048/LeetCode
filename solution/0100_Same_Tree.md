- 解法1
使用递归的方法。先判断当前节点是否都为空，如果都为空返回True；如果一个空一个不为空，返回False；如果都不为空，在判断值是否相同，如果值不同，返回False，如果值相同，递归判断p和q的左右子树。

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
        if p is None and q is None: # 都为空
            return True

        elif p and q: # 先判断节点值是否相等，再遍历左右子树
            if p.val != q.val:
                return False
            else:
                return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)

        else: # 一个空，一个不空
            return False
```