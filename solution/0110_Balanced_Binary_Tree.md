```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        def get_depth(root, depth):
            """
            获取一棵树的最大深度
            """
            if root is None:
                return depth
            else:
                depth += 1
                return max(get_depth(root.left, depth), get_depth(root.right, depth))
                

        if root is None:
            return True

        else:
            # 获取左子树的最大深度和右子树的最大深度，判断两者是否符合balance的条件
            left_depth = get_depth(root.left, 0)
            right_depth = get_depth(root.right, 0)
            if abs(left_depth - right_depth) > 1: # 如果不符合条件，返回False
                return False
            else: # 如果符合条件，继续递归root的左子树和右子树
                return self.isBalanced(root.left) and self.isBalanced(root.right)

        
```