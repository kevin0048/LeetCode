- 解法1：
递归，每次取子序列中间的作为根节点，左边的序列递归到根节点的左子树，右边的序列递归到根节点的右子树

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> TreeNode:
        def func(pt, l, r):
            if l>r:
                return
            if l==r:
                pt.val = nums[l]
                return
            mid = (l+r)>>1
            pt.val = nums[mid]
            if l<mid:
                pt.left = TreeNode(None)
                func(pt.left, l, mid-1)
            if mid<r:
                pt.right = TreeNode(None)
                func(pt.right, mid+1, r)
                
        root = TreeNode(None)
        n = len(nums)
        if n==0:
            return 
        func(root, 0, n-1)
        return root
```