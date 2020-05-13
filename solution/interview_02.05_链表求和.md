```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        res = ListNode(None)
        p = res
        bit = 0

        while l1 and l2:
            cur_val = l1.val + l2.val + bit
            bit = cur_val // 10
            cur_val %= 10
            p.next = ListNode(cur_val)
            l1, l2, p = l1.next, l2.next, p.next

        while l1:
            cur_val = l1.val + bit
            bit = cur_val // 10
            cur_val %= 10
            p.next = ListNode(cur_val)
            l1, p = l1.next, p.next
        while l2:
            cur_val = l2.val + bit
            bit = cur_val // 10
            cur_val %= 10
            p.next = ListNode(cur_val)
            l2, p = l2.next, p.next

        if bit:
            p.next = ListNode(1)

        return res.next
```