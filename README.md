# graph-routing-algos

This repository contains implementation of different algorithms:
1.  Dijkstra's algorithm

2. Bellman-Ford algorithm

3. Floyd-Warshall algorithm
   
# Dijkstra's Algorithm Implementation

An efficient implementation of Dijkstra's algorithm for finding the shortest paths from a source node to all other nodes in a weighted directed graph.

![Dijkstra Algorithm Visualization](https://github.com/yourusername/dijkstra-algorithm/raw/main/images/dijkstra_stages.png)

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

The repository includes a specific example that demonstrates how Dijkstra's algorithm processes a graph step-by-step, as illustrated in the included images:

![Dijkstra's Algorithm Steps](https://github.com/yourusername/dijkstra-algorithm/raw/main/images/dijkstra_steps.png)

The example traces through each step of the algorithm, showing:
- Which nodes are visited
- How distances are updated
- The contents of the priority queue
- The final shortest path tree

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/dijkstra-algorithm.git

# Navigate to the directory
cd dijkstra-algorithm

```

