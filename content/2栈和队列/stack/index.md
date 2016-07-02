---
title: 栈
prev: /2栈和队列
next: /2栈和队列/queue
weight: 5
---

这里我们只是简单实现一下栈的api,在不考虑性能的情况下，用python的list完全可以实现
```python
class Stack:
    def __init__(self,datas=[]):
        self.datas = datas

    def __len__(self):
        return len(self.datas)

    def isEmpty(self):
        return len(self) == 0

    def push(self,data):
        self.datas.append(data)

    def pop(self):
        return self.datas.pop() if not self.isEmpty() else None

    def peek(self):
        return self[len(self.datas)-1] if not self.isEmpty() else None

    def __getitem__(self,i):
        return self.datas[i]

    def __setitem__(self,i,y):
        self.datas[i] = y
```
