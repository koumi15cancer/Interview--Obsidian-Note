We can think of a heap as an array with a special property: the smallest value in the array is always in the first index of the array.

If we remove the smallest value from the heap, the elements of the array efficiently re-arrange so that the next smallest value takes its place at the front of the array.

Heaps are most frequently used in coding interviews to solve a class of problems known as "Top K" problems, which involve finding the k smallest or largest elements in a collection of elements.

These two representations of a heap are **equivalent**. The binary tree representation is a more intuitive way to understand how a heap works. But during the coding interview, you will most likely be working with the array representation of a heap, as it more efficient to work with.

Heaps are **complete binary trees**, which means that all levels of the tree are fully filled except for the last level, which is filled from left to right.


Left: A valid heap, right: an invalid heap.

Since heaps are complete binary trees, the **height of a heap is O(log n)**, where n is the number of elements in the heap. This is an important property to keep in mind when analyzing the time complexity of heap operations.


### Parent-Child Relationship

|Node|Index|
|---|---|
|Left Child|2 * i + 1|
|Right Child|2 * i + 2|
|Parent|⌊(i - 1) / 2⌋ (floor division)|

For example, for the node at index i = 2:

- The left child L is at index 2 * 2 + 1 = 5:
    
- The right child R is at index 2 * 2 + 2 = 6:
    
- The parent P is at index ⌊(2 - 1) / 2⌋ = 0:

![[Screenshot 2024-10-09 at 7.53.02 PM.png]]

## Heap Operations

A heap supports the following operations:

- _push(element)_: Add a new element to the heap.
    
- _pop()_: Remove the root element from the heap.
    
- _peek()_: Get the root element without removing it.
    
- _heapify([elements])_: Convert an array into a heap in-place.



### Summary

**If you only takeaway one thing from this section, remember that the pop and push operations both have a time complexity of O(log n).** The worst case for each operation involves swapping elements from the root of the heap to the last level of the tree, or vice versa, which takes O(log n) time.

| Operation | Time Complexity | Notes                                                               |
| --------- | --------------- | ------------------------------------------------------------------- |
| pop       | O(log n)        | Visualize bubbling down the new root to the last level of the tree. |
| push      | O(log n)        | Visualize bubbling up the new element to the root of the tree.      |
| peek      | O(1)            | Access the root of the heap.                                        |
| heapify   | O(n)            | Just memorize this!                                                 |

## Python HeapQ Module

Python provides a built-in module called [heapq](https://docs.python.org/3/library/heapq.html) that we can use to turn arrays into min-heaps.

The heapify function can be used to convert an array into a heap in-place. The heappush and heappop functions are used to push and pop elements from the heap, respectively.


#### Usage

```python
import heapq

arr = [3, 1, 4, 1, 5, 9, 2]

# convert array into a heap in-place. O(n)
heapq.heapify(arr)

# push 0 to the heap. O(log n)
heapq.heappush(arr, 0)

# peek the min element = 0. O(1)
arr[0]

# pop and return the min element = 0. O(log n)
min_element = heapq.heappop(arr)

# peek the new min element = 1. O(1)
arr[0]

```


#### Max Heap

By default, the heapq module creates a min-heap. To create a max-heap, we can negate the values in the list and then convert it into a heap using the heapify function. We also need to remember to negate the values when we push and pop elements from the heap.

```python
import heapq

arr = [3, 1, 4, 1, 5, 9, 2]

# negate the values in the array

negated_arr = [-x for x in arr]

# convert array into a min-heap

heapq.heapify(negated_arr) 

# push 11 to the heap by negating it

heapq.heappush(negated_arr, -11)

# peek root of heap = -11

negated_arr[0]

# pop and return the max element = -11

max_element = -heapq.heappop(negated_arr)

# peek the new max element = 9

negated_arr[0]

```

#### Storing Tuples

The heapq module can also be used to store tuples in the heap. By default, the heap is ordered based on the first element of the tuple. If the first elements are equal, the second elements are compared, and so on.

```python
import heapq

arr = [(3, 1), (1, 5), (4, 2), (1, 9), (5, 3), (9, 4), (2, 6)]
heapq.heapify(arr)

# pop and return the min element = (1, 5)
min_element = heapq.heappop(arr)

# peek the new min element = (1, 9)
arr[0]

# push (1, 7) to the heap, which is smaller than (1, 9)
heapq.heappush(arr, (1, 7))

# peek the min element = (1, 7)
arr[0]

```

## Use Case

#### Top-K Largest Elements in an Array
