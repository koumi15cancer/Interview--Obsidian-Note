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


#### [Graphs](https://www.hellointerview.com/learn/code/depth-first-search/graphs)

We then look at the two most common ways graphs are represented during the coding interview, and how to traverse both representations with DFS. Then we work through problems that give us practice with the different types of graph problems that can be solved using DFS.

During the coding interview, graphs are typically represented in two ways: as an adjacency list or as a matrix. So to best prepare for the coding interview, **you should be very comfortable with implementing basic DFS on both types of graphs** (meaning you can can write the code quickly, and without errors). From there, it's a matter of practicing enough graph questions to get a feel for the types of questions you might encounter.

When working with DFS on a graph, the most important thing to remember is to keep track of the visited nodes as you traverse, since graphs (unlike trees) can contain cycles.


## Adjacency List

An adjacency list is a common way to represent a graph. In an adjacency list, we are given a list of nodes, where each node is mapped to a list of its neighbors.

In Python, we can create an adjacency list using a dictionary where the keys are the nodes and the values are the list of nodes each node is connected to.

