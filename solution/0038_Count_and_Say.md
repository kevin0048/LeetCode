```python
class Solution:
    def countAndSay(self, n: int) -> str:
        result = "1"
        
        for i in range(1,n):
            # 解析初始result，生成新的result
            tmp_result = ""
            j = 0
            while j < len(result):
                count = 1
                if j == len(result)-1:
                    tmp_result = tmp_result +  "1"+str(result[j])
                    break
                
                for k in range(j+1, len(result)):
                    if result[j]==result[k]:
                        count+=1
                    else:
                        break
                
                tmp_result = tmp_result + str(count) + result[j]
                j += count
            result = tmp_result
        return result
```