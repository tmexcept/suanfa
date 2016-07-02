---
title: 队列
prev: /2栈和队列/stack/
next: /2栈和队列/commonquestion
weight: 10
---

这里我们只是简单实现一下队列的api,在不考虑性能的情况下，用python的list完全可以实现

## 简单队列
队列主要的api包括入队，出队，以及查看队首元素
```python
class Queue:
    def __init__(self,datas=[]):
        self.datas = datas

    def __len__(self):
        return len(self.datas)

    def isEmpty(self):
        return len(self) == 0

    def enqueue(self, data):
        self.datas.append(data)

    def dequeue(self):
        return self.datas.pop(0) if not self.isEmpty() else None

    def peek(self):
        return self[0] if not self.isEmpty() else None

    def __getitem__(self,i):
        return self.datas[i]

    def __setitem__(self,i,y):
        self.datas[i] = y
```

## 双端队列
和简单队列不同的是，双端队列两边都可以插入和删除。
```python
class Deque:
    def __init__(self,datas=[]):
        self.datas = datas

    def __len__(self):
    	return len(self.datas)

    def isEmpty(self):
    	return len(self) == 0

    def enqueue(self, data):
        self.datas.append(data)

    def dequeue(self):
        return self.datas.pop(0) if not self.isEmpty() else None

    def enqueueFront(self, data):
        self.datas.insert(0, data)

    def dequeueBack(self):
        return self.datas.pop() if not self.isEmpty() else None

    def peekFront(self):
        return self[0] if not self.isEmpty() else None

    def peekBack(self):
    	return self[len(self)-1]  if not self.isEmpty() else None

    def __getitem__(self,i):
    	return self.datas[i]

    def __setitem__(self,i,y):
    	self.datas[i] = y
```
