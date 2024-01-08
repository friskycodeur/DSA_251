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