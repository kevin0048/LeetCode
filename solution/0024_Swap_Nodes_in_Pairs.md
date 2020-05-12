```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def swapPairs(self, head: ListNode) -> ListNode:
        p = ListNode(None)
        p.next = head
        q = p 

        while head and head.next:
            p.next = head.next
            head.next = head.next.next
            p.next.next = head

            p = head
            head = head.next

        return q.next
            
```