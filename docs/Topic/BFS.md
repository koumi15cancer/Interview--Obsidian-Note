Breadth-First Search (BFS) is the next traversal algorithm we'll cover. BFS is a level-by-level traversal algorithm that starts at a node in a tree or graph-like data structure and processes all nodes at the current level before moving to the nodes at the next level.

-------
#### [Binary Trees](https://www.hellointerview.com/learn/code/breadth-first-search/fundamentals)

We start by learning how breadth-first search traverses the nodes in a binary tree, which will teach us the fundamentals of the algorithm. We then look at practice problems that are best solved using BFS.

#### BFS Procedure

BFS uses a **queue** to keep track of the nodes it needs to visit, and follows these steps:

- Start at the root node and add it to the queue.
    
- While the queue is not empty, remove the node at the front of the queue and visit it.
    
- Add the children of the node to the back queue.
    
- Repeat steps 2 and 3 until the queue is empty, which means you've processed all nodes in the tree.
    

**Queues in Python**

In Python, you can use the deque class from the collections module to create a queue.

The deque class provides an append method to add elements to the end of the queue and a popleft method to remove elements from the front of the queue, both of which run in O(1) time.


```python
def bfs(root):
  if not root:
    return []

  result = []
  queue = deque([root])

  while queue:
    curr_node = queue.popleft()
    result.append(curr_node.val)
    
    if curr_node.left:
      queue.append(curr_node.left)
    if curr_node.right:
      queue.append(curr_node.right)

  return result


```

```python
from collections import deque

class Solution:
    def bfs_template(self, root: Optional[TreeNode]):
        if not root:
            return []

        # Initialize the result list
        result = []

        # Initialize the queue with the root node
        q = deque([root])

        # Process the BFS level by level
        while q:
            # Get the number of nodes at the current level
            level_size = len(q)
            
            # Initialize a list to store the nodes of the current level (optional, based on the problem)
            current_level = []

            # Process all nodes at the current level
            for i in range(level_size):
                # Pop the front node from the queue
                curr_node = q.popleft()

                # Process the current node (customize this step based on the problem)
                current_level.append(curr_node.val)  # Example: storing node values

                # Add the children of the current node to the queue for the next level
                if curr_node.left:
                    q.append(curr_node.left)
                if curr_node.right:
                    q.append(curr_node.right)

            # Append the processed current level to the result (optional, based on the problem)
            result.append(current_level)  # Example: level order traversal

        return result


```

-------
#### [Graphs](https://www.hellointerview.com/learn/code/breadth-first-search/graphs)

We then look at the two most common ways graphs are represented during the coding interview, and how to traverse both representations with BFS. Then we work through problems that give us practice with the different types of graph problems that are best solved using BFS.

Just like with depth-first search, the most important thing to remember when implementing BFS on a graph is to keep track of visited nodes to avoid infinite loops. If we try to enqueue a node that has already been visited, we should skip it instead of adding it to the queue.

## BFS on an Adjacency List

To traverse a graph represented with an adjacency list with BFS:

- Choose a starting node and add it to the queue (we start with the first node in the adjacency list Node "1" in the example below).
    
- While the queue is not empty, remove the node at the front of the queue and add it to the set of visited nodes.
    
- Add the children of the node to the back of the queue (if they haven't been visited yet).
    
- Repeat steps 2 and 3 until the queue is empty.


```python
def bfs(start):
  visited = set([start])
  queue = [start]

  while queue:
    node = queue.pop(0)
    for neighbor in adjList[node]:
      if neighbor not in visited:
        visited.add(neighbor)
        queue.append(neighbor)

```


## BFS on an Matrix (2D Grid)

To traverse a graph represented as a matrix with BFS:

- Choose a starting node and add it to the queue (we start with top left node in the example below).
    
- While the queue is not empty, remove the node at the front of the queue and add it to the set of visited nodes.
    
- Add the four neighbors of the node to the back of the queue (if they haven't been visited yet and are within the bounds of the matrix).
    
- Repeat steps 2 and 3 until the queue is empty.

```python

def bfs(grid):
  visited = set()
  # up, down, left, right
  directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]

  queue = [(0, 0)]
  visited.add((0, 0))

  while queue:
    row, col = queue.pop(0)

    # enqueue neighbors
    for dr, dc in directions:
      n_row = row + dr
      m_col = col + dc

      # check bounds and if neighbor is visited
      if 0 <= n_row < len(grid) \
                and 0 <= m_col < len(grid[0]) \
                and (n_row, m_col) not in visited:
        queue.append((n_row, m_col))
        visited.add((n_row, m_col))

```


## Nodes at a Level

Like binary trees, graphs can also have levels. In a graph, a level is defined as the number of edges between the root node and the current node, which is also known as the "distance" between the two nodes.

This is the primary use case of BFS in graphs: to solve questions that involve traversing the graph level-by-level, so we should be familiar with this pattern for both adjacency lists and matrices.

![[Screenshot 2024-10-14 at 7.09.50 PM.png]]

And just like binary trees, the BFS algorithm can be extended to know when we have finished processing all nodes at a level. We can do this by adding a for-loop that iterates over the size of the queue at the beginning of each level.

### Adjacency List Level-By-Level

```python
from collections import deque

def bfs_levels(graph, start):
    queue = deque([start])
    visited = set()
    visited.add(start)
    levels = []

    while queue:
        level_size = len(queue)
        current_level = []

        for _ in range(level_size):
            node = queue.popleft()
            current_level.append(node)
            for neighbor in graph[node]:
                if neighbor not in visited:
                    visited.add(neighbor)
                    queue.append(neighbor)
        
        # IMPORTANT
        # we have finished processing all nodes at the current level
        levels.append(current_level)

    return levels

```

### Matrix Level-By-Level

```python
from collections import deque

def bfs_level_by_level(matrix):
    rows, cols = len(matrix), len(matrix[0])
    directions = [(0, 1), (1, 0), (0, -1), (-1, 0)]

    # start at the top-left corner
    queue = deque([(0, 0)])
    visited = set([(0, 0)])

    levels = []
    while queue:
        level_size = len(queue)
        current_level = []

        for _ in range(level_size):
            row, col = queue.popleft()
            current_level.append((row, col))
            for dr, dc in directions:
                r, c = row + dr, col + dc
                if 0 <= r < rows and 0 <= c < cols and (r, c) not in visited:
                    visited.add((r, c))
                    queue.append((r, c))

        # IMPORTANT
        # we have finished processing all nodes at this level
        levels.append(current_level)

    return levels

```

### Shortest Path in a Graph

A consequence of the level-by-level nature of BFS traversal is that we can use it to find the shortest path between two nodes in a graph. Because BFS traverses the graph level-by-level, the first time we reach the destination node will be on the shortest path between the two nodes.



