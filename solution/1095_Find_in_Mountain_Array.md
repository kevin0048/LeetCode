- 解法1
先用二分法找到最大值。
再用二分法遍历最大值左边的序列，这个序列是一个递增序列，如果找到了target对应的index，直接返回；
同样地使用二分法遍历最大值右边的序列，这是一个递减序列。

```python
# """
# This is MountainArray's API interface.
# You should not implement it, or speculate about its implementation
# """
#class MountainArray:
#    def get(self, index: int) -> int:
#    def length(self) -> int:

class Solution:
    def findInMountainArray(self, target: int, mountain_arr: 'MountainArray') -> int:
        n = mountain_arr.length()
        l, r = 0, n-1
        while l<r:
            mid = int((l+r+1)//2) # +1是为了把中间值往边上移一下
            if mountain_arr.get(mid) > mountain_arr.get(mid-1): # 如果中间值比左边的一个要大，那么最大值的区间在中间值的右边，否则在左边
                l = mid 
            else:
                r = mid - 1
        
        # 使用二分法处理最大值左边的序列
        top_index = l
        l, r = 0, top_index
        while l<r:
            mid = int((l+r)//2)
            cur_num = mountain_arr.get(mid)
            if cur_num == target:
                return mid
            elif cur_num > target:
                r = mid  # 因为mid总是小于r的，所以可以用r=mid，而不会导致死循环
            else:
                l = mid + 1 # 因为mid是大于等于l的，所以l=mid+1，这样不会导致死循环
                
        l, r = top_index, n-1
        while l<r:
            mid = int((l+r)//2)
            cur_num = mountain_arr.get(mid)
            if cur_num == target:
                return mid
            elif cur_num > target:
                l = mid + 1
            else:
                r = mid
                
        return l if mountain_arr.get(l)==target else -1 # 如果target在边界上
```