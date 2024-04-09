# Graph

A graph is a data structure that consists of a finite set of vertices (nodes) and a collection of edges that connect pairs of vertices. A graph can be directed or undirected, depending on whether the edges have a direction or not.

Applications of a graph include:

- Social networks.
- Maps and navigation systems.
- Computer networks.
- Recommendation systems.

Properties of a graph:

- **Vertex (Node)**: A fundamental unit of a graph.
- **Edge**: A connection between two vertices.
- **Weighted / Unweighted**: A value assigned to an edge.
- **Degree / Undirected**: The number of edges connected to a vertex.

## Storage Methods

There are two common ways to represent a graph:

- **Adjacency Matrix**: A 2D array of size `V x V` where `V` is the number of vertices in the graph. If there is an edge between vertices `i` and `j`, then `adjMatrix[i][j] = 1`, otherwise `adjMatrix[i][j] = 0`.
- **Adjacency List**: An array of lists is used. The size of the array is equal to the number of vertices. An entry `adjList[i]` represents the list of vertices adjacent to the `i`-th vertex.

### Differences between Adjacency Matrix and Adjacency List

-------------------------------------------------
| Operation | Adjacency Matrix | Adjacency List |
|-----------|-------------------|---------------|
|Add Vertex    | O(V^2) | O(1)     |
|Add Edge      | O(1)   | O(1)     |
|Remove Vertex | O(V^2) | O(V)     |
|Remove Edge   | O(1)   | O(V)     |
|Query         | O(1)   | O(V)     |
|Storage       | O(V^2) | O(V + E) |
-------------------------------------------------

#### **Adjacency Matrix**

- Uses more space.
- Iterating over all edges is slower.
- Finding the specific edge takes `O(1)` time.

#### **Adjacency List**

- Uses less space.(If data is sparse)
- Iterating over all edges is faster.
- Finding the specific edge takes `O(V)` time.

## Operations

Using an adjacency list to represent a graph, because data is usually sparse in real-world applications.

- **Add Vertex**: Add a new vertex to the graph.
- **Add Edge**: Add an edge between two vertices.
- **Remove Vertex**: Remove a vertex from the graph.
- **Remove Edge**: Remove an edge between two vertices.
- **Graph Traversal**: Visiting / Updating / Checking each vertex in a graph.
  - **Depth First Graph Traversal**: Visit all the vertices of a graph using a depth-first approach.
    - Stack: first in, last out.(FILO)
  - **Breadth First Graph Traversal**: Visit all the vertices of a graph using a breadth-first approach.
    - Queue: first in, first out.(FIFO)

```cpp
// C++ program to demonstrate graph
class Graph {
    constructor() {
        this.adjList = {};
        }

    // Add a vertex to the graph
    addVertex(vertex) {
        if (!this.adjList[vertex]) {
            this.adjList[vertex] = [];
        }
    }
    
    // Add an edge between two vertices
    addEdge(v2, v2) {
        this.adjList[v1].push(v2);
        this.adjList[v2].push(v1);
    }

    // Remove an edge between two vertices
    removeEdge(v1, v2) {
        this.adjList[v1] = this.adjList[v1].filter(v => v !== v2);
        this.adjList[v2] = this.adjList[v2].filter(v => v !== v1);
    }

    // Remove a vertex from the graph
    removeVertex(vertex) {
        while (this.adjList[vertex].length) {
            const adjacentVertex = this.adjList[vertex].pop();
            this.removeEdge(vertex, adjacentVertex);
        }
        delete this.adjList[vertex];
    }

    // Depth First Recursive Traversal
    depthFirstRecursive(start) {
        const result = [];
        const visited = {};
        const adjList = this.adjList;

        (function dfs(vertex) {
            if (!vertex) return null;
            visited[vertex] = true;
            result.push(vertex);
            adjList[vertex].forEach(neighbor => {
                if (!visited[neighbor]) {
                    return dfs(neighbor);
                }
            });
        })(start);

        return result;
    }

    // Depth First Iterative Traversal
    depthFirstIterative(start) {
        const stack = [start];  // Use a stack to keep track of vertices
        const result = [];
        const visited = {};
        let currentVertex;

        visited[start] = true;
        while (stack.length) {
            currentVertex = stack.pop();
            result.push(currentVertex);

            this.adjList[currentVertex].forEach(neighbor => {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    stack.push(neighbor);
                }
            });
        }

        return result;
    }

    // Breadth First Traversal
    breadthFirst(start) {
        const queue = [start];  // Use a queue to keep track of vertices
        const result = [];
        const visited = {};
        let currentVertex;
        visited[start] = true;

        while (queue.length) {
            currentVertex = queue.shift();
            result.push(currentVertex);

            this.adjList[currentVertex].forEach(neighbor => {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    queue.push(neighbor);
                }
            });
        }

        return result;
    }
}

```

## References

-[資料結構學習筆記 — 7. Graph](https://medium.com/@amber.fragments/%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B-%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98-7-graph-%E5%9C%96-d4359fb6f19a)
