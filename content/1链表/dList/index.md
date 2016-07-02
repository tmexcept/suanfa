---
title: 双向链表
prev: /1链表/singlelist
next: /1链表/commonquestion
weight: 10
---

双向链表和单链表不同之处在于，链表中的每一个节点，都保存其数据域和前/后驱指针。这就意味着如果你想删除链表的最后一个元素，你不需要从表头开始遍历到最后一个元素了。你可以直接从表尾开始直接删除这个元素。显然，双向链表在效率上要高于单链表，不过其数据结构更复杂，占用了更多的空间。

![DlinkedList](/img/ch1/dlinkedlist.pngpwd)

首先我们来定义节点。包含数据以及prev/next两个指针
```python
class Node:
    def __init__(self,data,next=None,prev=None):
        self.data = data
        self.next = next
        self.prev = prev
```

下面我们还是写出基本框架
```python
class DlinkedList:

    def __init__(self,datas=None):
        pass
    def __len__(self):
        pass
    def is_empty(self):
        pass
    def clear(self):
        pass
    def insert(self):
        pass
    def delete(self):
        pass
```

首先我们写出初始化函数
```python
def __init__(self,datas=None):

    if datas is None:
        self.head = None
        self.tail = None
        return

    if len(datas) == 1:
        node = Node(datas[0])
        self.head = node
        self.tail = self.head
        return

    self.head = Node(datas[0])
    self.tail = Node(datas[-1])
    p = self.head

    for data in datas[1:-1]:
        q = Node(data)
        p.next = q
        p.next = q
        q.prev = p

    p.next = self.tail
    self.tail.prev = p
```

主要需要注意的是插入和删除，我们需要判断插入位置是靠近头还是尾

```python
def insert(self, index, data):

    if data is None:
        return

    if index < 0 or index > len(self):
        return

    if self.is_empty() and index == 0:
        q = Node(data)
        self.head = q
        self.tail = self.head
        return

    if index == 0:
        q = Node(data, self.head, None)
        self.head.prev = q
        self.head = q
        return

    if index == len(self):
        q = Node(data, None, self.tail)
        self.tail.next = q
        self.tail = q
        return

    if index <= len(self) / 2:
        j = 0
        p = self.head
        post = self.head
        while j < index:
            post = p
            p = p.next
            j += 1
        q = Node(data, p, post)
        post.next = q
        p.prev = q
        return

    if index > len(self) / 2:
        j = len(self)
        p = self.tail
        post = self.tail
        while j > index:
            post = p
            p = p.prev
            j -= 1
        q = Node(data, post, p)
        post.prev = q
        p.next = q


def delete(self, index):

    if index < 0 or index >= len(self):
        return

    if index == 0:
		    result = self.head.data
        self.head = self.head.next
        return result

    if index == len(self) - 1:
        result = self.tail.data
        self.tail = self.tail.prev
        return result

    if index <= len(self)/2:
        j = 0
        p = self.head
        post = self.head
        while j < index:
            post = p
            p = p.next
            j += 1
        post.next = p.next
        p.next.prev = post
        return p.data

    if index > len(self)/2:
        j = len(self)-1
        p = self.tail
        post = self.tail
		    while j > index:
            post = p
            p = p.prev
            j = j-1
        post.prev = p.prev
        p.prev.next = post
        return p.data
```
