- 解法1
首先计算两个数组长度，计算平均值m，根据平均值的奇偶性来判断中位数是第m个还是 第m-1和第m个平均值；然后遍历两个数组，每遍历一个，判断是否达到中位数的位置，这个通过一个count变量和中位数位置m、奇偶c来判断
```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        l1 = len(nums1)
        l2 = len(nums2)
        m = (l1+l2)//2
        c = 1 if m==(l1+l2)/2 else 0 # 如果如果l1+l2是偶数，中位数为m-1,m;如果是奇数，中位数为m
        count = 0
        
        l3 = l4 = 0
        n1 = None
        while l3<l1 and l4 < l2:
            if nums1[l3] < nums2[l4]:
                cur_num = nums1[l3]
                l3 += 1
            else:
                cur_num = nums2[l4]
                l4 += 1
            
            if c == 1 and m-1 == count:
                n1 = cur_num
            if c == 1 and m == count:
                return (n1+cur_num)/2
            if c==0 and m==count:
                return cur_num
            
            count += 1
            
        while l3 < l1:
            cur_num = nums1[l3]
            if c == 1 and m-1 == count:
                n1 = cur_num
            if c == 1 and m == count:
                return (n1+cur_num)/2
            if c==0 and m==count:
                return cur_num
            l3 += 1
            count += 1
            
        while l4 < l2:
            cur_num = nums2[l4]
            if c == 1 and m-1 == count:
                n1 = cur_num
            if c == 1 and m == count:
                return (n1+cur_num)/2
            if c==0 and m==count:
                return cur_num
            l4 += 1
            count += 1
```