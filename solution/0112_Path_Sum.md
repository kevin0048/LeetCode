- 解法1
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def hasPathSum(self, root: TreeNode, sum: int) -> bool:
        ret = []

        def func(root, cur_sum):
            if root.left:
                func(root.left, cur_sum + root.val)
            if root.right:
                func(root.right, cur_sum + root.val)
            if root.left is None and root.right is None:
                ret.append(cur_sum+root.val)


        if root is None:
            return False
        func(root, 0)
        return True if sum in ret else False
```
