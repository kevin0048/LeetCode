- 解法1
将链表数据复制到数组中，然后通过数组比较是否为回文。时间复杂度O(n)，空间复杂度O(n)
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def isPalindrome(self, head: ListNode) -> bool:
        data = []
        while head:
            data.append(head.val)
            head = head.next

        return data==data[::-1]
```

- 解法2
使用双指针遍历链表，f和l初始都指向head，前指针f一次走两步，后指针l一次走一步；f遍历到最后有两种情况：当链表节点个数是奇数时，f刚好是最后一个node，当链表节点个数是偶数时，f.next是最后一个node

然后将后面一半的链表进行反转，然后再遍历前一半链表和后一半链表是否相等。如果链表节点数是奇数，不用管中间那个节点

```python
class Solution:
    def reverse(self, head):
        if head is None or head.next is None:
            return head

        p = self.reverse(head.next)

        head.next.next = head
        head.next = None

        return p
    
    def equal(self, p, q):
        while p and q:
            if p.val != q.val:
                return False
            else:
                p, q = p.next, q.next
        return True

    def isPalindrome(self, head:ListNode) -> bool:
        if head is None or head.next is None:
            return True
        
        f = l = head
        while 1:
            if not f.next or not f.next.next:
                middle = l.next
                break
                
            else:
                f = f.next.next
                l = l.next
                
        p = self.reverse(middle)
        return self.equal(p, head)
```
