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

## 3. Merging Two Linked Lists

The last operation is merging two linked lists. As an example of this operation, we'll look at how to merge two sorted linked lists.

As an input to this problem, we are given the heads of two sorted linked lists, l1 and l2, and we need to return the head of a new linked list that contains all the nodes from the two input linked lists in sorted order.

To merge two sorted linked lists, we start by determining the head of the merged linked list by comparing the values of l1 and l2, and setting the head to the smaller of the two nodes. We then advance l1 = l1.next or l2 = l2.next depending on which node we chose as the head of the merged linked list.


```python

def merge_lists(l1, l2):
  if not l1: return l2
  if not l2: return l1

  if l1.val < l2.val:
    head = l1
    l1 = l1.next
  else:
    head = l2
    l2 = l2.next

  tail = head
  while l1 and l2:
    if l1.val < l2.val:
      tail.next = l1
      l1 = l1.next
    else:
      tail.next = l2
      l2 = l2.next
    tail = tail.next

  tail.next = l1 or l2
  return head

```

## Dummy Nodes

Merging two sorted linked lists is an example of a problem where using a dummy node can simplify the logic of the code.

Notice that in the solution for merging two lists above, the logic for choosing the head of the merged linked list is the same as the logic for choosing the next node to append. We need to handle it as a special case because without it, we wouldn't have a starting point for the merged linked list.

We can avoid this by creating a dummy node to represent the starting point of the merged linked list. This allows us to move directly into the iteration processes without having to introduce a special case to initialize the head of the merged linked list. When the iteration finishes we return dummy.next as the head of the merged linked list.

Note: The term "dummy node" refers to creating a new node that isn't part of the input linked list(s) (line 2 in the code below).


```python

def merge_two_lists(l1, l2):
  dummy = ListNode()
  tail = dummy

  while l1 and l2:
    if l1.val < l2.val:
      tail.next = l1
      l1 = l1.next
    else:
      tail.next = l2
      l2 = l2.next
    tail = tail.next

  tail.next = l1 or l2
  return dummy.next

```