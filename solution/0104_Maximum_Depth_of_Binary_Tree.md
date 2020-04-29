- 递归
如果根节点为空，返回0，否则返回max(左子树深度,右子树深度)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        def func(root, max_d):
            if root is None:
                return max_d
            if root is not None:
                max_d += 1
                return max(func(root.left, max_d), func(root.right, max_d))
        if root is None:
            return 0
        else:
            return max(func(root.left, 1), func(root.right, 1))
```
