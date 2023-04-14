# Adjacency Matrix

An adjacency matrix is a square matrix used to represent a finite graph in which the elements represent the edges between the nodes. The adjacency matrix has a row and a column for each node in the graph, and the value at the intersection of a row and column indicates the presence (usually a 1) or absence (usually a 0) of an edge between those nodes.

Here's an example of an adjacency matrix for a simple undirected graph with 4 nodes (A, B, C, and D) and the following edges: (A, B), (A, C), and (C, D).

|   | A | B | C | D |
|:-:|:-:|:-:|:-:|:-:|
| A | 0 | 1 | 1 | 0 |
| B | 1 | 0 | 0 | 0 |
| C | 1 | 0 | 0 | 1 |
| D | 0 | 0 | 1 | 0 |

The adjacency matrix is symmetric for undirected graphs since the edges are bidirectional. For directed graphs, the matrix might not be symmetric, as the presence of an edge from one node to another does not guarantee the presence of an edge in the opposite direction.

In addition to the basic concept of adjacency matrices, there are a few more properties and concepts that you should be aware of:

**Weighted graphs**: In weighted graphs, edges have associated weights or costs. The adjacency matrix of a weighted graph will store the weight of the edge between two nodes instead of a binary value. For example, consider a weighted graph with 4 nodes (A, B, C, and D) and the following edges with weights: (A, B, 3), (A, C, 2), and (C, D, 4).

Here's the adjacency matrix for this weighted graph:

|   | A | B | C | D |
|:-:|:-:|:-:|:-:|:-:|
| A | 0 | 3 | 2 | 0 |
| B | 3 | 0 | 0 | 0 |
| C | 2 | 0 | 0 | 4 |
| D | 0 | 0 | 4 | 0 |

**Operations on adjacency matrices**: You can perform various matrix operations on adjacency matrices to compute different properties of the graph. For example, you can multiply two adjacency matrices to find the number of paths of a certain length between nodes.

**Time complexity**: The adjacency matrix representation of a graph has a time complexity of O(V^2) for most operations, where V is the number of vertices in the graph. This is because you need to access every element in the matrix to perform operations like adding or removing an edge, or checking if an edge exists between two nodes. This representation is efficient for dense graphs, where the number of edges is close to V^2. However, it can be inefficient for sparse graphs, where the number of edges is much smaller than V^2.

**Alternatives to adjacency matrices**: An alternative way to represent graphs is the adjacency list representation. An adjacency list consists of an array or list of vertices, where each vertex has a list of its neighboring vertices. This representation is more space-efficient for sparse graphs and can have better time complexity for certain graph operations, depending on the specific use case.

In summary, adjacency matrices are a useful way to represent graphs, especially for dense graphs or when you need to perform matrix operations. However, for sparse graphs or when space efficiency is a concern, you may want to consider other representations like adjacency lists.