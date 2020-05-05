- 递归
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isValidBST(self, root: TreeNode) -> bool:
        def func(root, lower=float("-inf"), upper=float("inf")):
            if not root:
                return True
            val = root.val
            if val <= lower or val >= upper:
                return False
            if not func(root.left, lower, val):
                return False
            if not func(root.right, val, upper):
                return False
            return True

        return func(root)
```

- 中序遍历
```python
class Solution:
    def isValidBST(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        stack, inorder = [], float('-inf')
        
        while stack or root:
            while root:
                stack.append(root)
                root = root.left
            root = stack.pop()
            # 如果中序遍历得到的节点的值小于等于前一个 inorder，说明不是二叉搜索树
            if root.val <= inorder:
                return False
            inorder = root.val
            root = root.right

        return True

```