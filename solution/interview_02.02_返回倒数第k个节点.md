```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def kthToLast(self, head: ListNode, k: int) -> int:
        tot_num = 0
        p = head
        while p:
            tot_num += 1
            p = p.next

        while tot_num - k:
            head = head.next
            tot_num -= 1

        return head.val
```