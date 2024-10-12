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