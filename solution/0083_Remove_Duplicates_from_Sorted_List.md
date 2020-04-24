- 解法
使用前后双指针遍历链表

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        if head and head.next:
            second = head
            first = second.next
            while first:
                if second.val == first.val:
                    first = first.next
                else:
                    second.next = first
                    second = second.next
                    first = first.next
            second.next = first # 重点，如果后面几个数字都是重复的，first会指向None，要把second.next指向first
            return head
            
        else:
            return head
```
