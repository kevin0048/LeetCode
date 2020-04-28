- 解法1
抖机灵，使用python list的in和index方法
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        if target in nums:
            return nums.index(target)
        else:
            return -1
```

- 解法2
利用两段数组都是排序数组的特点
1. 如果数组长度为0，返回-1
2. 遍历数组，记录数组开头start0，数组最大值end0
    1. 如果第i个数字等于target，返回i
    2. 如果第i个数字小于开头，而且target<第i个数字，说明此时已经遍历到了第二段，第二段开头的数字是最小的，如果target比最小的数字还小，那么返回-1
    3. 同样，如果遍历到了第二段，而且target比第一段最大的数字还大的话，返回-1
    
算法的平均时间复杂度应该是O(log(n))，空间复杂度O(1)

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        if len(nums) == 0:
            return -1
        
        start0 = nums[0]
        end0 = 0
        for i in range(len(nums)):
            if target == nums[i]:
                return i
            if nums[i]<start0 and target < nums[i]:
                return -1
            end0 = end0 if nums[i]< end0 else nums[i]
            
            if nums[i] < start0 and target > end0:
                return -1
        return -1

```
