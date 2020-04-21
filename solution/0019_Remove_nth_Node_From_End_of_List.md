先遍历一遍链表，计算长度；然后使用双指针再次遍历链表，删除指定节点

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        total_n = 0
        pointer = head
        while pointer:
            total_n += 1
            pointer = pointer.next

        if n==1 and total_n==1:
            return None
        
        elif n==total_n:
            return head.next
        
        else:
            last_pointer = head
            fast_pointer = last_pointer.next

            idx =  0
            while fast_pointer:
                if idx+1 == total_n - n:
                    last_pointer.next = fast_pointer.next
                    return head
                else:
                    last_pointer = fast_pointer
                    fast_pointer = fast_pointer.next
                    idx += 1

```
