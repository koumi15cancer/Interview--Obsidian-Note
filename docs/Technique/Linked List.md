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

## 1. Fast and Slow Pointers

Fast and slow pointers is a technique that is used to find the middle node in a linked list. We initialize two pointers, slow and fast, that start at the head of the linked list. We then iterate until fast reaches the end of the list. During each iteration, the slow pointer advances by one node, while the fast pointer advances by two nodes. When the fast pointer reaches tail of the list, the slow pointer points to the middle node.


```python
def findTarget(head):
    slow = head
    fast = head

    while fast and fast.next:
        slow = slow.next         # Move slow pointer by 1 step
        fast = fast.next.next    # Move fast pointer by 2 steps
        
        # Condition to meet or detect a cycle
        if slow == fast:
            return True  # Or perform the required action

    return False  # Or return the result (if needed)


```

### Key Concepts:

1. **Initialization**:
    
    - Both pointers start at the same position, typically the head of a linked list or the start of an array.
2. **Traversal**:
    
    - The **slow pointer** moves one step at a time.
    - The **fast pointer** moves two steps at a time.
3. **Cycle Detection**:
    
    - If there’s a cycle, the fast pointer will eventually meet the slow pointer inside the cycle.
    - If no cycle exists, the fast pointer will reach the end (e.g., `fast == None` or `fast.next == None` in the case of linked lists).

## 2. Reversing a Linked List

Reversing a linked list involves changing the direction of the next pointers in a linked list so the last node becomes the head of the reversed linked list.

The algorithm for reversing a linked list is an iterative algorithm which involves 3 pointers, prev, current, and next_.

1. current points to the node we are currently reversing.
    
2. prev is the last node that was reversed, and also the node that current.next will point to after reversing.
    
3. next_ is the next node we will reverse. We need a pointer to this node before we overwrite the current.next so we can continue reversing the list in the next iteration.

```python

def reverse(head):
  prev = None
  current = head
  while current:
    next_ = current.next
    current.next = prev
    prev = current
    current = next_

  return prev

```