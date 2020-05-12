```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def middleNode(self, head: ListNode) -> ListNode:
        if head is None or head.next is None:
            return head

        f = l = head
        while 1:
            if f.next is None:
                return l
            elif f.next.next is None:
                return l.next
            else:
                f = f.next.next
                l = l.next
```