
```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        len_nums= len(nums)
        i, val_count = 0, 0
        while i < len_nums-val_count:
            if nums[i]==val:
                nums[i], nums[len_nums-val_count-1] = nums[len_nums-val_count-1], nums[i]
                val_count += 1
            else:
                i+=1
        return len_nums-val_count

```