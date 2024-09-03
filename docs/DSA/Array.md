# 1. Components
- Array Name
- Data Type
- Element

# 2. Complexity
- Access : 1 ( by index)
- Search: n 
- Search ( sorted ): Logn
- Insert: n
- Insert ( at the end): 1
- Remove: n
- Remove ( at the end ): 1

# 3.Common term
- Subarray: [2,4,5,7] -> subarray is [4,5,7]
- Subsequence: [2,4,5,7] -> subsequence is [2,5,7]

# 4. Considering points in interview
- Duplicate value in array ? affect answer -> make it harder or easier 
- Use index to iterate -> consider out of bounds
- Mindful : slicing and concatenate -> take N times | Start and End indices to demarcate subarray/ range

# 5. Corner Case
- Empty cases
- Sequence with 1 - 2 elements
- Sequence with repeated elements
- Duplicated values in sequence

# 6.Techniques
- [[Traversing more than one]]
- [[Index as hash key]]
- [[Precomputation]]
- [[Traversing from the right]]
- [[Two pointers]]
- [[Sliding Window]]