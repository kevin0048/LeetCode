# [两数相加](https://leetcode-cn.com/problems/add-two-numbers/)
- 解法1：遍历
这个解法还是比较简单的，先从低位到高位同时遍历l1和l2的节点，直到l1=None或l2=None，然后遍历l1剩下的节点和l2剩下的节点，需要注意的是满10要向高位进1

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        bit = 0

        result = ListNode(None)
        cur_pointer = result
        while l1 and l2:
            val, bit = (l1.val + l2.val + bit)%10, (l1.val + l2.val + bit)//10
            cur_pointer.next = ListNode(val)
            l1, l2, cur_pointer = l1.next, l2.next, cur_pointer.next
            
        while l1:
            val, bit = (l1.val + bit)%10, (l1.val + bit)//10
            cur_pointer.next = ListNode(val)
            l1, cur_pointer = l1.next, cur_pointer.next

        while l2:
            val, bit = (l2.val + bit)%10, (l2.val + bit)//10
            cur_pointer.next = ListNode(val)
            l2, cur_pointer = l2.next, cur_pointer.next

        if bit:
            cur_pointer.next = ListNode(1)

        return result.next
        
```

- 解法2
鸡贼解法，把链表拼成字符串，再相加，然后再生成链表，可以AC，但是算法层面上0分，因为这道题主要考核单向链表的知识
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        a = ""
        b = ""
        while l1:
            a = str(l1.val) + a
            l1 = l1.next
            
        while l2:
            b = str(l2.val) + b
            l2 = l2.next
            
        c = int(a) + int(b)

        result = ListNode(None)
        pointer = result
        for i in str(c)[::-1]:
            pointer.next = ListNode(int(i))
            pointer = pointer.next
            
        return result.next
        
```
