## Basics

A linked list is a data structure consisting of sequence of a nodes, where each node contains a value and reference to the next node in the sequence.

In Python, we can represent a linked list node with a ListNode class, where val is a piece of data and next is a reference to the next node in the linked list.

# Definition of a ListNode

```python
# Definition of a ListNode
class ListNode:
  def __init__(self, val=0, next=None):
    self.val = val
    self.next = next
```