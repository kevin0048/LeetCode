```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reverse(self, head: ListNode) -> ListNode:
        if head is None or head.next is None:
            return head

        p = self.reverse(head.next)
        head.next.next = head
        head.next = None
        return p

    def equal(self, p: ListNode, q: ListNode) -> ListNode:
        while p:
            if p.val != q.val:
                return False
            else:
                p, q = p.next, q.next

        return True

    def isPalindrome(self, head: ListNode) -> bool:
        if head is None or head.next is None:
            return True

        f = l = head
        while 1:
            if f.next is None or f.next.next is None:
                middle = l.next
                break
            else:
                f, l = f.next.next, l.next

        return self.equal(self.reverse(middle), head)

```