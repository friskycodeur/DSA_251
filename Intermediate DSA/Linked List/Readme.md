## [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

### Solution - Python (Recursion)

```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head or not head.next:
            return head
        
        xyz = self.reverseList(head.next)
        head.next.next = head
        head.next = None
        return xyz
```

### Solution - Python (Iterative)

```python
def reverseLinkedList(head):
    prev,curr= None,head
    while curr!=None:
        nextt,curr.next = curr.next,prev
        prev,curr = curr,nextt
    
    head = prev
    return head
```
## [Middle Of Linked List](https://www.codingninjas.com/studio/problems/middle-of-linked-list_973250)

### Solution - Python

```python
'''
    class Node:
        def __init__(self, data):
            self.data = data
            self.next = None
'''
def findMiddle(head):
    fast = head
    while fast!=None and fast.next!=None:
        head = head.next
        fast = fast.next.next
    
    return head
```

## [Add Two Linked Lists](https://www.codingninjas.com/studio/problems/add-two-numbers-as-linked-lists_1170520)

### Solution - Python

```python
'''
class Node:
    def __init__(self, data=0, next=None):
        self.data = data
        self.next = next
'''
def addTwoNumbers(head1: Node, head2: Node) -> Node:
    node = Node()
    start = node
    rem = 0
    while (head1!=None or head2!=None) or rem: 
        currNodeSum = 0
        if(head1!=None):
            currNodeSum+=head1.data
            head1 = head1.next
        if(head2!=None):
            currNodeSum+=head2.data
            head2 = head2.next       
        currNodeSum += rem
        rem = currNodeSum//10
        resNode = Node(currNodeSum%10)
        start.next = resNode
        start = start.next

    return node.next
```

## [Delete Kth node from End](https://leetcode.com/problems/remove-nth-node-from-end-of-list)

### Solution - Python

```python
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        start = ListNode()
        start.next = head
        fast = slow = start
        for i in range(1,k+1):
            fast = fast.next
        while fast.next!=None:
            fast = fast.next
            slow = slow.next
        slow.next = slow.next.next
        return start.next
```

## [Detect and Remove Loop](https://www.codingninjas.com/studio/problems/interview-shuriken-42-detect-and-remove-loop_241049)

### Solution - Python

```python
def removeLoop(head :Node) -> Node :
    fast = slow = head
    while fast!=None and fast.next !=None:
        fast = fast.next.next
        slow = slow.next
        if (fast == slow):
            slow.next = None
            break
    return head
```

## [Swap Nodes in Pairs](https://www.codingninjas.com/studio/problems/pair-swap_759396)

### Solution - Python

```python
def pairsSwap(head):
    if head!=None and head.next!=None:
        # Swap data of pairs
        head.data,head.next.data = head.next.data,head.data
        # Call for next pair
        pairsSwap(head.next.next)
    return head
```

## [Segregate Odd-Even](https://www.codingninjas.com/studio/problems/segregate-odd-even_920524)

### Solution - Python

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

def segregateOddEven(head):
    evenStart = oddStart = oddEnd = evenEnd = None
    current = head
    while current is not None:
        num = current.data
        if(num%2==0):
            if(evenStart is None):
                evenStart = current
                evenEnd = evenStart
            else:
                evenEnd.next = current
                evenEnd = evenEnd.next
        else:
            if(oddStart is None):
                oddStart = current
                oddEnd = oddStart
            else:
                oddEnd.next = current
                oddEnd = oddEnd.next
        current = current.next
    
    if oddStart is None and evenStart is not None:
        evenEnd.next = None
        head = evenStart
    elif oddStart is not None and evenStart is None:
        oddEnd.next = None
        head = oddStart
    else:
        oddEnd.next = evenStart
        evenEnd.next = None
        head = oddStart
    return head

