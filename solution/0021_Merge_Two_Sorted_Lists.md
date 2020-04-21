```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        result = ListNode(None)
        pointer = result
        while l1 and l2:
            if l1.val <= l2.val:
                pointer.next = ListNode(l1.val)
                pointer, l1 = pointer.next, l1.next
            else:
                pointer.next = ListNode(l2.val)
                pointer, l2 = pointer.next, l2.next

        while l1:
            pointer.next = ListNode(l1.val)
            pointer, l1 = pointer.next, l1.next
        while l2:
            pointer.next = ListNode(l2.val)
            pointer, l2 = pointer.next, l2.next

        return result.next
```