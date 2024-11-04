
### Summary of Key Templates:

- **Basic Traversal**: Nested loops for cell access.
- **Four Directions Traversal**: For visiting neighboring cells.
- **DFS / BFS**: For region-based or connected components.
- **Binary Search**: For sorted matrices.
- **Matrix Rotation**: Using transpose and reverse.
- **Spiral Order Traversal**: Top, right, bottom, left bounds.
- **Dynamic Programming**: For path or sum calculations.



### 1. **Basic Traversal Template**

Matrix problems often require traversing each element. Use nested loops to visit each cell.

```python
for i in range(len(matrix)):
    for j in range(len(matrix[0])):
        # Process matrix[i][j]


```

### 2. **Four Directions Traversal**

When the problem requires visiting adjacent cells (top, bottom, left, right), this pattern is useful:

```python
# Define directions: (up, down, left, right)
directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]

for i in range(len(matrix)):
    for j in range(len(matrix[0])):
        for direction in directions:
            ni, nj = i + direction[0], j + direction[1]
            if 0 <= ni < len(matrix) and 0 <= nj < len(matrix[0]):
                # Process matrix[ni][nj]

```

### 3. **DFS / BFS for Matrix**

Matrix problems that involve regions (e.g., connected cells) can often be solved with DFS or BFS.

#### DFS Template:

```python
def dfs(i, j):
    # Base case
    if i < 0 or j < 0 or i >= len(matrix) or j >= len(matrix[0]) or matrix[i][j] != target_value:
        return
    # Mark the cell as visited
    matrix[i][j] = visited_value
    # Recursively visit neighbors
    for direction in directions:
        dfs(i + direction[0], j + direction[1])

for i in range(len(matrix)):
    for j in range(len(matrix[0])):
        if matrix[i][j] == target_value:
            dfs(i, j)


```

#### BFS Template:

```python
from collections import deque

def bfs(i, j):
    queue = deque([(i, j)])
    while queue:
        i, j = queue.popleft()
        # Process (i, j)
        matrix[i][j] = visited_value
        for direction in directions:
            ni, nj = i + direction[0], j + direction[1]
            if 0 <= ni < len(matrix) and 0 <= nj < len(matrix[0]) and matrix[ni][nj] == target_value:
                queue.append((ni, nj))

for i in range(len(matrix)):
    for j in range(len(matrix[0])):
        if matrix[i][j] == target_value:
            bfs(i, j)


```


### 4. **Binary Search in a Sorted Matrix**

For a sorted matrix, especially when each row is sorted and each column is sorted, binary search can be used.

#### Binary Search on Row and Column Sorted Matrix:

```python
def searchMatrix(matrix, target):
    if not matrix or not matrix[0]:
        return False
    row, col = 0, len(matrix[0]) - 1
    while row < len(matrix) and col >= 0:
        if matrix[row][col] == target:
            return True
        elif matrix[row][col] > target:
            col -= 1
        else:
            row += 1
    return False



```

### 5. **Rotating a Matrix**

If you need to rotate a matrix 90 degrees clockwise, transpose and then reverse each row.

```python
def rotate(matrix):
    # Transpose
    for i in range(len(matrix)):
        for j in range(i, len(matrix[0])):
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
    # Reverse each row
    for i in range(len(matrix)):
        matrix[i].reverse()

```

### 6. **Spiral Order Traversal**

A common problem involves visiting elements in a spiral order.

```python
def spiralOrder(matrix):
    result = []
    top, bottom, left, right = 0, len(matrix) - 1, 0, len(matrix[0]) - 1

    while top <= bottom and left <= right:
        for j in range(left, right + 1):
            result.append(matrix[top][j])
        top += 1

        for i in range(top, bottom + 1):
            result.append(matrix[i][right])
        right -= 1

        if top <= bottom:
            for j in range(right, left - 1, -1):
                result.append(matrix[bottom][j])
            bottom -= 1

        if left <= right:
            for i in range(bottom, top - 1, -1):
                result.append(matrix[i][left])
            left += 1

    return result


```

### 7. **Dynamic Programming on a Matrix**

When the problem requires calculating paths, sums, or specific values for each cell based on neighboring cells, dynamic programming (DP) is often applied.

#### Example: Minimum Path Sum

```python
def minPathSum(grid):
    rows, cols = len(grid), len(grid[0])
    dp = [[0] * cols for _ in range(rows)]
    dp[0][0] = grid[0][0]

    # Initialize first row and first column
    for i in range(1, rows):
        dp[i][0] = dp[i-1][0] + grid[i][0]
    for j in range(1, cols):
        dp[0][j] = dp[0][j-1] + grid[0][j]

    # Fill DP table
    for i in range(1, rows):
        for j in range(1, cols):
            dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + grid[i][j]

    return dp[-1][-1]


```