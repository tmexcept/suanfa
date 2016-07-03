---
title: 常见问题
prev: /2栈和队列/queue/
next: /3树
weight: 15
toc: true
---

## valid Parenthese
[leetcode 20题](https://leetcode.com/problems/valid-parentheses/) 题目要求我们判断一个字符串是否为有效的括号组。"{[]()()}"是一个有效的括号组，而"{()[}"并不是。

我们可以用栈来帮助我们实现。当我们遇到左括号的时候我们将其压入栈中，当我们遇到右括号的时候，我们让栈顶元素出栈，并查看得到的左括号是否和当前的右括号匹配，如果遇到右括号而当前栈为空的话，显然也可以直接判断这个字符串不是有效的括号组


```python
class Solution(object):
    def isValid(self, s):
        dict = {"}":"{","]":"[",")":"("}
        stack = []
        for st in s:
            if st in dict.values():
                stack.append(st)
            elif len(stack)>0:
                p = stack.pop()
                if p != dict[st]:
                    return False
            else:
                return False
        return stack == []
```

## basic calculator
[leetcode 224题](https://leetcode.com/problems/basic-calculator/)

## maximal rectangle
[leetcode 85题](https://leetcode.com/problems/maximal-rectangle/)
