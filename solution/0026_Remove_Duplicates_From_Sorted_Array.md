使用两个指针，第一个指针指向当前无重复数组的最后一位，第二个指针遍历数组，当两个指针指向的数字不一样的时候，第一个指针往前移一位，同时修改第一个指针的数值为第二个指针指向的数值；最后返回第一个指针+1（因为index从0开始）

```
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        len_nums = len(nums)
        
        if len_nums <= 1:
            return len_nums
        
        i = 0
        
        for j in range(1, len_nums):
            if nums[i] != nums[j]:
                i += 1
                nums[i] = nums[j]
                
        return i+1
```
