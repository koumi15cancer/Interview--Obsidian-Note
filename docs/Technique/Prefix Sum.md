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