The stack data structure is a collection of elements that follow the Last-In, First-Out (LIFO) principle, which means that the last element added to the stack is the first one to be removed.

Elements that are added to the stack are said to be "pushed" onto the stack, while elements that are removed are said to be "popped" from the stack. Both of these operations take O(1) time.

### Using an Array as a Stack

Arrays are frequently used to implement stacks, with the end of the array acting as the top of the stack.

In Python, the append and pop array methods can be used to push and pop elements from the stack


# Monotonic Stack

A **monotonic stack** is a special type of stack in which all elements on the stack are sorted in either descending or ascending order. It is used to solve problems that require finding the next greater or next smaller element in an array.

##  Problem: Next Greater Element

```python
def nextGreaterElement(nums):
  n = len(nums)
  result = [-1] * n
  stack = []

  for i in range(n):
    while stack and nums[i] > nums[stack[-1]]:
      idx = stack.pop()
      result[idx] = nums[i]
    stack.append(i)

  return result

```

## Next Smaller Element

```python

def nextSmallerElement(nums):
  n = len(nums)
  result = [-1] * n
  stack = []

  for i in range(n):
    while stack and nums[i] < nums[stack[-1]]:
      idx = stack.pop()
      result[idx] = nums[i]
    stack.append(i)

  return result

```