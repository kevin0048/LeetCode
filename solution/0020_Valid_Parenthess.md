遍历字符串，把左括号放到栈里面去，每当遍历到一个右括号，pop一下栈，看看pop出来的左括号是否与右括号匹配，匹配则继续遍历，不匹配return False，如果栈为空，也return False；最后如果栈为空，return True，否则return False

```python
class Solution:
    def isValid(self, s: str) -> bool:
        if len(s)==0:
            return True
        
        valid_pair = {
            "(":")",
            "{":"}",
            "[":"]"
        }
        
        left = ["{", "(", "["]
        right = ["}", ")", "]"]
        
        stack = list()
        
        for i in range(len(s)):
            if s[i] in left:
                stack.append(s[i])
            else:
                if len(stack):
                    if valid_pair[stack.pop()] == s[i]:
                        pass
                    else:
                        return False
                else:
                    return False
        if len(stack):
            return False
        return True

```
