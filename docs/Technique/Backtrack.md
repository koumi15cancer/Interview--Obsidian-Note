Backtracking algorithms use [Depth-First Search](https://www.hellointerview.com/learn/code/depth-first-search/introduction) to search all possible paths for a solution to a path.

## Template Backtracking matrix

```python
def backtrack(matrix, row, col, path):
    # Base case: If we've reached a stopping condition (e.g., goal or invalid state)
    if is_goal(matrix, row, col):
        # Handle the found solution (e.g., save path or update a result)
        result.append(list(path))  # Example: Save the current path
        return

    # Mark the current cell as visited (or any other modification needed)
    visited.add((row, col))
    path.append((row, col))

    # Define movement directions in a matrix (up, down, left, right)
    directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]

    for dr, dc in directions:
        new_row, new_col = row + dr, col + dc

        # Check if new position is within bounds and not visited
        if 0 <= new_row < len(matrix) and 0 <= new_col < len(matrix[0]) and (new_row, new_col) not in visited:
            # Recursive call: move to the next cell
            backtrack(matrix, new_row, new_col, path)

    # Backtrack: undo the current move (unmark the current cell)
    visited.remove((row, col))
    path.pop()

def solve(matrix):
    result = []
    visited = set()

    # Starting point: you can loop through the matrix to handle multiple starts
    for row in range(len(matrix)):
        for col in range(len(matrix[0])):
            if is_valid_start(matrix, row, col):
                backtrack(matrix, row, col, [])

    return result



```


## Solution-Space Trees

In the Overview section, we use Depth-First Search to explore all valid root-to-leaf paths in a binary tree that we are given. In most backtracking problems, we won't be given an explicit tree to traverse. Instead, our algorithm needs to construct the tree based on the problem.