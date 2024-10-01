Keep the start and end state of the window 

# Variable-Length

## Template

```python
def variable_length_sliding_window(nums):
  state = # choose appropriate data structure
  start = 0
  max_ = 0

  for end in range(len(nums)):
    # extend window
    # add nums[end] to state in O(1) in time

    while state is not valid:
      # repeatedly contract window until it is valid again
      # remove nums[start] from state in O(1) in time
      start += 1

    # INVARIANT: state of current window is valid here.
    max_ = max(max_, end - start + 1)

  return max_


```
# Fixed-Length

Consider using the sliding window pattern for questions that involve **searching for a continuous subsequence** in an array or string that satisfies a certain constraint.

If you know the length of the subsequence you are looking for, use a fixed-length sliding window. Otherwise, use a variable-length sliding window.

_Examples:_

- Finding the largest substring without repeating characters in a given string (variable-length).
    
- Finding the largest substring containing a single character that can be made by replacing at most k characters in a given string (variable-length).
    
- Finding the largest sum of a subarray of size k without duplicate elements in a given array (fixed-length).

## Template

```python
def fixed_length_sliding_window(nums, k):
  state = # choose appropriate data structure
  start = 0
  max_ = 0

  for end in range(len(nums)):
    # extend window
    # add nums[end] to state in O(1) in time

    if end - start + 1 == k:
      # INVARIANT: size of the window is k here.
      max_ = max(max_, contents of state)

      # contract window
      # remove nums[start] from state in O(1) in time
      start += 1

  return max_


```

