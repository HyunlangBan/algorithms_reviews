## Queue와 Stack 구현해보기
간단하지만 확실하게 알아두기!
### Queue
```python
class Queue:
    def __init__(self):
        self.queue = []

    def isEmpty(self):
#         if self.queue == []:
#             return True
#         else:
#             return False
        return self.queue == []

    def enqueue(self,data):
        self.queue.append(data)

    def dequeue(self):
        data = self.queue[0]
        del self.queue[0]
        return data

    def peek(self):
        return self.queue[0]

    def sizeQueue(self):
        return len(self.queue)


```

### Stack
```python
class Stack:
    def __init__(self):
        self.stack = []

    def isEmpty(self):
        return self.stack == []

    def push(self, data):
        self.stack.append(data)

    def pop(self):
        data = self.stack[-1]
        del self.stack[-1]
        return data

    def peek(self):
        return self.stack[-1]

    def sizeStack(self):
        return len(self.stack)


```
