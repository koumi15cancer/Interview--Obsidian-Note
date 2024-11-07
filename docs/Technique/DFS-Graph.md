
```python
def dfs_recursive(graph, node, visited):
    # Base case: If the node has already been visited, return
    if node in visited:
        return
    
    # Mark the node as visited
    visited.add(node)
    
    # Process the node (you can perform any action you need here)
    print(node)  # Example action: print the node
    
    # Recursively visit all adjacent nodes
    for neighbor in graph[node]:
        dfs_recursive(graph, neighbor, visited)

# Usage:
# graph = {
#     0: [1, 2],
#     1: [0, 3, 4],
#     2: [0],
#     3: [1],
#     4: [1]
# }
# visited = set()
# dfs_recursive(graph, starting_node, visited)


```