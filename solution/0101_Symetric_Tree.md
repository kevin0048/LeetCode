- 解法1：递归
如果左右子树都是空的，返回True；如果左右子树都非空，而且值相等，递归 l.left,r.right  和 l.right,r.left；如果值不相等，返回False；如果一个子树空另一个不空，返回False

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        def func(l, r):
            if l is None and r is None:
                return True
            elif l is not None and r is not None:
                if l.val != r.val:
                    return False
                else:
                    return func(l.left, r.right) and func(l.right, r.left)
            else:
                return False

        if root is None:
            return True
        else:
            return func(root.left, root.right)
```

- 解法2：迭代
与递归相似，首先判断根节点是否为空，如果为空，直接返回True；然后将根节点的左右节点放到一个list中。
遍历左右子树，如果左右节点都为空，不处理；如果左右节点都不空，且值相等，再把l的左子树、r的右子树，l的右子树、r的左子树加到list中，要保证第一个pop出来的是右子树，第二个pop出来的是左子树；如果值不相等，返回False；如果一个空一个不空，返回False


```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        if root is None:
            return True

        deq = [root.left, root.right]
        while deq:
            r_right = deq.pop()
            r_left = deq.pop()

            if r_left is None and r_right is None:
                continue
            if r_left is None or r_right is None:
                return False
            if r_left and r_right:
                if r_left.val != r_right.val:
                    return False
                deq.extend([r_left.left, r_right.right, r_left.right, r_right.left])
        return True

```
