```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getDecimalValue(self, head: ListNode) -> int:
        def reverse(h):
            if h is None or h.next is None:
                return h

            p = reverse(h.next)

            h.next.next = h
            h.next = None

            return p

        p = reverse(head)
        bit = 0
        res = 0
        while p:
            res += p.val* 2 ** bit
            bit += 1
            p = p.next

        return res
```