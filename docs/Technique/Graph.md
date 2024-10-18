## Topological Sort

![[Screenshot 2024-10-18 at 1.03.25 PM.png]]

A given graph may have more than one valid topological sorts. We'll look at one algorithm for finding a topological sort - **Kahn's Algorithm**, which uses the concept of **indegrees**.

### Indegrees

Each node in a graph has an **indegree**, which is the number of incoming edges to that node.![[Screenshot 2024-10-18 at 1.04.21 PM.png]]

##### Calculate Indegrees

**List of Edges**

If our graph is given to us as list of edges, we can calculate the indegree of each node by iterating through the edges and incrementing the indegree of the destination node.

```python
def indegree(n, edges): 
    indegree = [0] * n
    for u, v in edges:
        indegree[v] += 1
    return indegree

```

**Adjacency List**

If our graph is given to us as an [adjacency list](https://www.hellointerview.com/learn/code/depth-first-search/adjacency-list), we can calculate the indegree of each node by iterating through the neighbors of each node and incrementing their indegree.

```python
def indegree(adj_list, n):
    indegree = [0] * n
    for u in adj_list:
        # increment the indegree of each neighbor of u
        for v in adj_list[u]:
            indegree[v] += 1

```


### Kahn's Algorithm

Kahn's algorithm is a form of [Breadth-First Search](https://www.hellointerview.com/learn/code/breadth-first-search/graphs) in which nodes with lower indegrees are placed on the queue before nodes with higher indegrees.

The algorithm is as follows:

1. Calculate the indegree of each node.
    
2. Add all nodes with an indegree of 0 to a queue.
    
3. While the queue is not empty:
    
    1. Dequeue the first node from the queue and add it to the topological order.
        
    2. For each neighbor of the node, decrement its indegree by 1. If the neighbor's indegree is now 0, add it to the queue.
        
    
4. Return the topological order.