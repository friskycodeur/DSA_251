## [Implement Stack Using Array](https://www.codingninjas.com/studio/problems/stack-implementation-using-array_3210209)

### Solution - Python

```python
from sys import *
from collections import *
from math import *
from typing import List

class Stack:
    def __init__(self, n: int):
        # Write your code here
        self.top_index  = -1
        self.capacity = n
        self.stack = [None]*n

    def push(self, num: int):
        if self.top_index  == self.capacity - 1:
            return
        self.top_index  +=1
        self.stack[self.top_index ] = num

    def pop(self) -> int:
        if self.top_index  == -1:
            return -1
        num = self.stack[self.top_index]
        self.top_index  -=1
        return num

    def top(self) -> int:
        if self.top_index  == -1:
            return -1
        return self.stack[self.top_index]

    def isEmpty(self) -> int:
        return self.top_index  == -1

    def isFull(self) -> int:
        return self.top_index  == self.capacity - 1
```

## [Implement Stack Using LinkedList](https://www.codingninjas.com/studio/problems/implement-stack-with-linked-list_630475)

### Solution - Python

```python
class Node:
    def __init__(self, data, next_node=None):
        self.data = data
        self.next = next_node

class Stack:
    def __init__(self):
        self.sz = 0
        self.head = Node("head")
        
    def getSize(self):
        return self.sz

    def isEmpty(self):
        return self.sz == 0

    def push(self, data):
        node = Node(data=data)
        node.next = self.head.next
        self.head.next = node
        self.sz +=1

    def pop(self):
        if self.isEmpty():
            raise Exception("Poping from Empty Stack")
        remove = self.head.next
        self.head.next = self.head.next.next
        self.sz -=1
        return remove

    def getTop(self):
        if self.isEmpty():
            raise Exception("Poping from Empty Stack")
        return self.head.next.data
```


## [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

### Solution - Python

```python
class Solution:
    def isValid(self, s: str) -> bool:
        parStack = []
        for pr in s:
            if pr in ('(','[','{'):
                parStack.append(pr)
            else:
                if len(parStack) == 0:
                    return False
                prInStack = parStack[-1]
                if (prInStack =='(' and pr == ')') or (prInStack =='[' and pr == ']') or (prInStack =='{' and pr == '}'):
                    parStack.pop()
                else:
                    return False

        return len(parStack) == 0  
```


## [ Implement a Queue](https://www.codingninjas.com/studio/problems/2099908)

### Solution - Python (Via Array)

```python
from os import *
from sys import *
from collections import *
from math import *

class Queue :
    #Define data members and __init__()
    
    def __init__(self):
        self.frontIdx = 0
        self.rear = 0
        # Taking custom capacity as 5000 as it is the max queries that can be made in the qsn
        self.capacity = 5000
        self.q = [None]*5000

    '''----------------- Public Functions of Queue -----------------'''
    
    def isEmpty(self) :
        #Implement the isEmpty() function
        return self.frontIdx == self.rear

    def enqueue(self, data) :
        #Implement the enqueue(element) function
        self.q[self.rear] = data
        self.rear +=1 

    def dequeue(self) :
        if self.isEmpty():
            return -1
        num = self.q[self.frontIdx]
        self.frontIdx +=1
        return num

    def front(self) :
        #Implement the front() function
        if self.isEmpty():
            return -1
        return self.q[self.frontIdx]
```


### Solution - Python (Via LinkedList)

```python
from os import *
from sys import *
from collections import *
from math import *

class Node:

    def __init__(self,data,nextNode=None):
        self.data = data
        self.next = nextNode

class Queue :

    def __init__(self):
        self.frontNode = self.rearNode = None

    '''----------------- Public Functions of Queue -----------------'''

    def isEmpty(self) :
        return self.frontNode == None

    def enqueue(self, data) :
        newNode = Node(data)
        if self.rearNode == None:
            self.rearNode = self.frontNode = newNode
        else:
            self.rearNode.next = newNode
            self.rearNode = newNode

    def dequeue(self) :
        if self.isEmpty():
            return -1
        deleteNode = self.frontNode
        self.frontNode = self.frontNode.next
        if(self.frontNode == None):
            self.rearNode = None
        return deleteNode.data

    def front(self) :
        if self.isEmpty():
            return -1
        return self.frontNode.data
```