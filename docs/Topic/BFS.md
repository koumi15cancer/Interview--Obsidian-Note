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



-------
#### [Graphs](https://www.hellointerview.com/learn/code/breadth-first-search/graphs)

We then look at the two most common ways graphs are represented during the coding interview, and how to traverse both representations with BFS. Then we work through problems that give us practice with the different types of graph problems that are best solved using BFS.