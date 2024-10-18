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

## Backtrack template

```python
def backtrack(path, options):
    # 1. Base Case: If a complete or valid solution is found
    if is_solution(path):
        process_solution(path)
        return

    # 2. Loop through all possible choices (remaining decisions)
    for option in options:
        if is_valid(option, path):  # 3. Prune invalid options early
            # Make a choice
            path.append(option)

            # Explore further with this choice
            backtrack(path, remaining_options(option, options))

            # Undo the choice (backtrack)
            path.pop()

def is_solution(path):
    # Define what constitutes a valid solution
    pass

def is_valid(option, path):
    # Prune out invalid options early
    pass

def remaining_options(option, options):
    # Define how the option list changes as choices are made
    pass

def process_solution(path):
    # Handle the solution (e.g., store it, print it)
    pass

# Initial call with the empty path and all available options
backtrack([], initial_options)


```

### Explanation:

- **`backtrack(path, options)`**: This function recursively builds possible solutions.
    - `path`: Stores the current state of the solution being constructed.
    - `options`: Represents the set of choices that can still be made at the current level of the solution space tree.
- **Base Case**: When a complete solution is found (e.g., a certain length is reached, or a goal is met), the base case is triggered, and the solution is processed.
- **Pruning**: Before making a decision (or adding an option to the path), we check whether the current option is valid given the state of the current path. If it isn't, we skip it.
- **Recursive Call**: Once a valid option is chosen, it is added to the path, and `backtrack` is called recursively to explore further.
- **Backtracking**: After exploring with the current choice, the choice is undone (popped from the path) to try other options.

### Summary

The first step in solving a backtracking problem is to visualize the solution-space tree.

- Each node in the solution-space tree corresponds to a single recursive call.
    
- The parameters of the recursive function correspond to the information needed to reach the neighbors of a node.
    
- The body of the recursive function should iterate over the neighbors of a node and make recursive calls for each neighbor.