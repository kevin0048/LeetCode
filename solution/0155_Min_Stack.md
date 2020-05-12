```python
class MinStack:

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.min_val = float("inf")
        self.stack = []


    def push(self, x: int) -> None:
        self.stack.append(x)
        self.min_val = self.min_val if self.min_val < x else x

    def pop(self) -> None:
        del self.stack[-1]
        if self.stack:
            self.min_val = min(self.stack)
        else:
            self.min_val = float("inf")

    def top(self) -> int:
        return self.stack[-1]


    def getMin(self) -> int:
        return self.min_val


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(x)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```