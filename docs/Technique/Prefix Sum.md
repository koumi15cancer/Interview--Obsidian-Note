A **prefix-sum** is a technique for efficiently calculating the sum of subarrays in an integer array.


### Calculating Prefix Sums

We can calculate the prefix-sums of an array in O(n) with the following algorithm:
```python
def prefix_sums(arr):

    n = len(arr)

    prefix = [0] * (n + 1)

    for i in range(1, n + 1):

        prefix[i] = prefix[i - 1] + arr[i - 1]

    return prefix

```

### Time Complexity

**Time Complexity**: O(n) to calculate the prefix-sums as we have to iterate through the array once. After that, calculating the sum of any subarray takes O(1) time.

**Space Complexity**: O(n) to store the prefix-sums.

## Template

```python
def prefix_sum(nums):
    # Step 1: Create the prefix sum array
    prefix = [0] * (len(nums) + 1)  # Extra element for easy calculation
    
    for i in range(len(nums)):
        prefix[i + 1] = prefix[i] + nums[i]
    
    # Step 2: Use the prefix sum array to calculate any range sum
    def range_sum(left, right):
        return prefix[right + 1] - prefix[left]  # Inclusive sum from `left` to `right`
    
    return range_sum

# Example usage:
nums = [3, 1, 4, 1, 5]
range_sum = prefix_sum(nums)

# Get sum of subarray from index 1 to 3
print(range_sum(1, 3))  # Output: 6 (1 + 4 + 1)
pr

```