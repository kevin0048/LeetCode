```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def removeDuplicateNodes(self, head: ListNode) -> ListNode:
        if head is None or head.next is None:
            return head
        p = head
        ret = [p.val]
        while p.next:
            if p.next.val in ret:
                if p.next.next:
                    p.next = p.next.next
                else:
                    p.next = None
                    return head
            else:
                ret.append(p.next.val)
                p = p.next
                
        return head
```
