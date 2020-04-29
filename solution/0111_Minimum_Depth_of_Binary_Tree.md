递归求法，要注意的是，怎么判断一个节点是叶子节点：它非空，且没有左右子树
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def minDepth(self, root: TreeNode) -> int:
        def func(root, depth):
            if root is None:
                return depth
            elif root.left and root.right:
                return min(func(root.left, depth+1), func(root.right, depth+1))
            elif root.left:
                return func(root.left, depth+1)
            elif root.right:
                return func(root.right, depth + 1)
            else:
                return depth + 1
                
        if root is None:
            return 0
        if root.left is None and root.right is None:
            return 1
        elif root.left is None:
            return func(root.right, 1)
        elif root.right is None:
            return func(root.left, 1)
        else:
            return min(func(root.left, 1), func(root.right, 1))
```