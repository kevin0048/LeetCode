- 解法1（超时）
自己想了使用递归的方法，超时了
```python
class Solution:
    def jump(self, nums) -> int:
        res = []
        def func(num_list, tot_step):
            if len(num_list) == 0:
                res.append(tot_step-1)
                
            elif len(num_list) == 1:
                res.append(tot_step)
                
            else:
                cur_num = num_list[0]
                if cur_num >= len(num_list):
                    res.append(tot_step+1)
                    return
                for i in range(1, cur_num+1):
                    func(num_list[i:], tot_step + 1)
        
        func(nums, 0)
        
        return min(res)
```

- 解法2，搬运官方解法
使用贪心算法，每次找到可以达到的最远位置。

```python
class Solution:
    def jump(self, nums) -> int:
        n = len(nums)
        maxPos = end = step = 0
        for i in range(n-1):
            if maxPos >= i: # 如果i符合当前可到达的所有位置，更新maxPos
                maxPos = max(maxPos, i+nums[i])
                if i == end: # 如果i到达了边界，更新边界，step+1
                    end = maxPos
                    step += 1
        return step
```