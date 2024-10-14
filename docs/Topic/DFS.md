Depth-First Search (DFS) is a traversal algorithm that visits all nodes in a tree or graph-like data structure. It can be applied to a wide variety of problems, making it the most important algorithm to know for the coding interview.

This module teaches you how to solve coding interview questions using depth-first search. It is divided into 2 sections:

#### [Binary Trees](https://www.hellointerview.com/learn/code/depth-first-search/fundamentals)

We start by learning how depth-first search traverses the nodes in a binary tree, which will teach us the fundamentals of the algorithm. We then learn how to solve binary tree interview questions using depth-first search and recursion, and apply what we learned by working through practice problems.

## Template 

```python
def dfs(node):

    # base case

    if node is None:

        return some value

    ...

    left = dfs(node.left)

    right = dfs(node.right)

    return value based on left and right
```

###  Passing Values Down and Helper Functions

In some cases, questions require us to pass information "down" from parents to child nodes, which we do via the parameters of our recursive function. If we need more parameters than the original function signature allows, then we need to introduce a helper function to help us recurse.

------

#### [Graphs](https://www.hellointerview.com/learn/code/depth-first-search/graphs)

We then look at the two most common ways graphs are represented during the coding interview, and how to traverse both representations with DFS. Then we work through problems that give us practice with the different types of graph problems that can be solved using DFS.

During the coding interview, graphs are typically represented in two ways: as an adjacency list or as a matrix. So to best prepare for the coding interview, **you should be very comfortable with implementing basic DFS on both types of graphs** (meaning you can can write the code quickly, and without errors). From there, it's a matter of practicing enough graph questions to get a feel for the types of questions you might encounter.

When working with DFS on a graph, the most important thing to remember is to keep track of the visited nodes as you traverse, since graphs (unlike trees) can contain cycles.


## Adjacency List

An adjacency list is a common way to represent a graph. In an adjacency list, we are given a list of nodes, where each node is mapped to a list of its neighbors.

In Python, we can create an adjacency list using a dictionary where the keys are the nodes and the values are the list of nodes each node is connected to.

#### Constructing Adjacency Lists

```python

def build_adj_list(n, edges):
    adj_list = {i: [] for i in range(n)}

    for u, v in edges:
        adj_list[u].append(v)
        adj_list[v].append(u)
        
    return adj_list
```

DFS for a graph is conceptually similar to DFS on a binary tree. The algorithm tries to go as deep as possible along a path before backtracking to explore other paths.

The key differences are:

1. Each node can have any amount of neighbors, so we need a for loop to iterate over each neighbor rather than making calls to the left and right children of the current node.
    
2. Because graphs can contain cycles, **we need to keep track of nodes we have already visited**. If we encounter a node that has already been visited, we should return immediately without making any further recursive calls (or skip it in the loop altogether). Otherwise, we may end up in an infinite loop.
    
3. We don't need an explicit base case like we do in the trees. Eventually, we will visit all nodes in the graph, and the recursion will stop on its own (with the help of the visited set).


### Template

```python

def dfs(adjList):
  if not adjList:
    return
  visited = set()

  def dfs_helper(node):
    if node in visited:
      return

    visited.add(node)
    for neighbor in adjList[node]:
      dfs_helper(neighbor)
    return

  dfs_helper(adjList[0])


```

- Use a set to keep track of visited nodes. Each time you visit a node, add it to the set.
    
- If you encounter a node that has already been visited, return immediately without making any further recursive calls.
    
- Use a for loop to iterate over each neighbor of the current node, and recursively call dfs on each neighbor.


Graph Cycle Detection Algorithm Template

```python
from typing import List

class GraphCycleDetector:
    def __init__(self, n: int, edges: List[List[int]]):
        self.n = n  # Number of nodes
        self.edges = edges  # List of undirected edges
        self.adj_list = [[] for _ in range(n)]  # Initialize adjacency list
        self.visited = [False] * n  # To track visited nodes
        
        # Build the adjacency list
        self.build_graph()

    def build_graph(self):
        """Builds the adjacency list for the graph from the list of edges."""
        for u, v in self.edges:
            self.adj_list[u].append(v)
            self.adj_list[v].append(u)

    def has_cycle(self) -> bool:
        """Returns True if the graph contains a cycle, False otherwise."""
        for node in range(self.n):
            if not self.visited[node]:  # Only start DFS if the node hasn't been visited
                if self.dfs(node, -1):  # Start DFS from the node, with no parent (-1)
                    return True
        return False

    def dfs(self, node: int, parent: int) -> bool:
        """Performs DFS and checks if there's a cycle in the graph."""
        self.visited[node] = True
        for neighbor in self.adj_list[node]:
            if not self.visited[neighbor]:  # If the neighbor hasn't been visited
                if self.dfs(neighbor, node):  # Recur for the neighbor
                    return True
            elif neighbor != parent:  # If the neighbor is visited and not the parent, it's a cycle
                return True
        return False

# Example Usage:
n = 5
edges = [[0, 1], [1, 2], [2, 3], [1, 3], [3, 4]]  # Example edges with a cycle

detector = GraphCycleDetector(n, edges)
print(detector.has_cycle())  # Output: True (because the graph contains a cycle)


```



------

### Matrices 
