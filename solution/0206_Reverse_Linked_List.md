- 解法1
迭代方法
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        if head is None:
            return head
        
        p = None
        while head:
            t = ListNode(head.val)
            head = head.next
            
            t.next = p
            p = t
        return p
```

- 解法2
递归方法
```python
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        if head is None or head.next is None:
            return head
        
        p = self.reverseList(head.next)
        head.next.next = head
        head.next = None
        return p
```