```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        i1 = 0
        
        for i in range(n):
            insert = False
            for j in range(i1,m+i):
                if nums2[i] <= nums1[j]:
                    # 从j开始，nums1往后面移位
                    k = m+i
                    while k>j:
                        nums1[k] = nums1[k-1]
                        k-=1
                        
                    nums1[j] = nums2[i]
                    i1 = j+1
                    insert = True
                    break
            if not insert:
                nums1[m+i] = nums2[i]
```
