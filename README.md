# graph-routing-algos

This repository contains implementation of different algorithms:
1.  Dijkstra's algorithm

2. Bellman-Ford algorithm

3. Floyd-Warshall algorithm
   
# Dijkstra's Algorithm Implementation

An efficient implementation of Dijkstra's algorithm for finding the shortest paths from a source node to all other nodes in a weighted directed graph.


## Overview

This repository contains a Python implementation of Dijkstra's algorithm, one of the most fundamental algorithms for finding shortest paths in graphs with non-negative edge weights. The implementation is designed to be both efficient and educational, with step-by-step visualization capabilities to help understand how the algorithm works.

## Features

- **Core Implementation**: Fast and memory-efficient implementation using a priority queue
- **Step-by-Step Visualization**: Option to see each step of the algorithm's execution
- **Detailed State Tracking**: Tracks visited nodes, current distances, and priority queue state
- **Verification Tools**: Tools to verify the algorithm against known examples
- **Comprehensive Documentation**: Well-documented code with clear explanations

## Usage

### Basic Usage

```python
# Define your graph as an adjacency list with weights
graph = {
    0: [(1, 10), (2, 5)],   # Node 0 connects to node 1 with weight 10 and node 2 with weight 5
    1: [(2, 2), (4, 1)],    # Node 1 connects to node 2 with weight 2 and node 4 with weight 1
    2: [(1, 3), (3, 2)],    # Node 2 connects to node 1 with weight 3 and node 3 with weight 2
    3: [(4, 4), (0, 7)],    # Node 3 connects to node 4 with weight 4 and node 0 with weight 7
    4: [(3, 6), (1, 9)]     # Node 4 connects to node 3 with weight 6 and node 1 with weight 9
}

# Run Dijkstra's algorithm from source node 0
from dijkstra import dijkstra
shortest_distances = dijkstra(graph, 0)

# Print the results
for node, distance in shortest_distances.items():
    print(f"Shortest distance from node 0 to node {node}: {distance}")
```

### Step-by-Step Visualization

```python
from dijkstra import run_dijkstra_with_steps
shortest_distances = run_dijkstra_with_steps(graph, 0)
```

## Algorithm Explanation

Dijkstra's algorithm finds the shortest path between a source node and all other nodes in a graph with non-negative weights. It works as follows:

1. Initialize distances to all nodes as infinity except the source node (distance = 0)
2. Add the source node to a priority queue
3. While the priority queue is not empty:
   - Extract the node with the minimum distance
   - For each neighbor of the extracted node:
     - Calculate potential new distance through the current node
     - If this new distance is shorter than the known distance, update it
     - Add the neighbor to the priority queue with its new distance
4. Return the distances to all nodes

The time complexity is O((V + E) log V) where V is the number of vertices and E is the number of edges.

## Example

The repository includes a specific example that demonstrates how Dijkstra's algorithm processes a graph step-by-step, as illustrated in the included image in the repository:


The example traces through each step of the algorithm, showing:
- Which nodes are visited
- How distances are updated
- The contents of the priority queue
- The final shortest path tree


# Bellman-Ford Algorithm Implementation

## Overview

This repository contains a Python implementation of the Bellman-Ford algorithm for finding shortest paths in a weighted directed graph. The algorithm is particularly valuable because it can handle graphs with negative edge weights and can detect negative cycles, unlike Dijkstra's algorithm.
The Bellman-Ford algorithm was developed by Richard Bellman and Lester Ford Jr. It computes shortest paths from a single source vertex to all other vertices in a weighted digraph. The main advantage over simpler algorithms like Dijkstra's is its ability to handle negative edge weights.

## Algorithm Details

### Time and Space Complexity
- **Time Complexity**: O(V×E) where V is the number of vertices and E is the number of edges
- **Space Complexity**: O(V) for storing distances and predecessors

### Key Steps
1. Initialize distances (source vertex to 0, all others to infinity)
2. Relax all edges |V|-1 times
3. Check for negative-weight cycles

### Edge Relaxation
The core operation in Bellman-Ford is edge relaxation: for an edge (u,v) with weight w, if `distance[u] + w < distance[v]`, then update `distance[v] = distance[u] + w` and set u as the predecessor of v.

## Implementation Notes

This repository includes two implementations:

1. **Standard Bellman-Ford**: A straightforward implementation that processes edges in arbitrary order
2. **Ordered Bellman-Ford**: A modified version that processes edges in a specified order, useful for educational purposes and debugging

### Important Considerations

- **Edge Processing Order**: The final shortest paths are independent of edge processing order, but intermediate results after each pass depend on this order
- **Negative Edges vs. Negative Cycles**: The algorithm handles negative edges correctly but will report if a negative cycle exists
- **Path Reconstruction**: Included utility for reconstructing the shortest path from source to any destination using the predecessor information

## Example

The implementation includes an example based on the graph shown in the algorithm visualization. This graph has:
- 5 vertices: s (source), t, x, y, z
- 10 edges, including negative edges (t→y: -4, t→z: -2, x→t: -2)

After running the algorithm, we get the shortest paths from source 's' to all other vertices:
- s→y→t = 2
- s→t→z→x = 4
- s→y = 7
- s→t→z = 2

## Usage

```python
# Define your graph as an adjacency list with edge weights
graph = {
    's': {'t': 6, 'y': 7},
    't': {'x': 5, 'y': -4, 'z': -2},
    'y': {'z': 9, 't': 8},
    'x': {'t': -2},
    'z': {'x': 7, 's': 2}
}

# Run the Bellman-Ford algorithm
source = 's'
distances, predecessors, has_negative_cycle = bellman_ford(graph, source)

# Print results
print(f"Shortest distances from {source}:")
for vertex, distance in distances.items():
    print(f"{vertex}: {distance}")

# Reconstruct a specific path
path = reconstruct_path(predecessors, source, 'x')
print(f"Path from {source} to x: {' → '.join(path)}")
```

## Visualization

The repository includes visualizations showing how the algorithm progresses through iterations:
1. **Initial State**: All vertices (except source) have distance = ∞
2. **Intermediate States**: After each pass of edge relaxations, showing how distances improve
3. **Final State**: The optimal distances and predecessors

The visualization demonstrates how negative edges can lead to path improvements in later iterations, highlighting why multiple passes are necessary.

## Edge Cases and Debugging

When implementing or using Bellman-Ford, watch out for:

1. **Detecting Negative Cycles**: The algorithm will identify if the graph contains any negative-weight cycles reachable from the source
2. **Unreachable Vertices**: Vertices not reachable from the source will maintain a distance of infinity
3. **Edge Relaxation Order**: If you're debugging or using the algorithm for educational purposes, be aware that intermediate results depend on the order of edge relaxations








## References

- Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (2009). Introduction to Algorithms (3rd ed.). MIT Press.

