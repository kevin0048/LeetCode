```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getKthFromEnd(self, head: ListNode, k: int) -> ListNode:
        tot_nums = 0
        p = head
        while p:
            tot_nums += 1
            p = p.next
        
        while tot_nums-k:
            head = head.next
            tot_nums -= 1

        return head
```