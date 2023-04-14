# Adjacency Matrix

An adjacency matrix is a square matrix that represents a graph. Each row and column of the matrix represents a vertex, and the values in the matrix indicate whether there is an edge between two vertices. If there is an edge between vertices i and j, then the (i, j) and (j, i) entries of the matrix are set to 1. If there is no edge between vertices i and j, then the (i, j) and (j, i) entries of the matrix are set to 0.

For example, consider the following graph:

   A --- B
  / \   / \
 C---D---E---F

We can represent this graph using an adjacency matrix as follows:

   A B C D E F
A  0 1 1 0 0 0
B  1 0 0 0 1 0
C  1 0 0 1 0 0
D  0 0 1 0 1 1
E  0 1 0 1 0 1
F  0 0 0 1 1 0

As you can see, the rows and columns of the matrix correspond to the vertices A through F, and the entries indicate whether there is an edge between each pair of vertices.

In some cases, we may also use a weighted adjacency matrix, where the entries represent the weight of the edge between two vertices instead of just 1 or 0.

To summarize, adjacency matrices are a useful tool for representing graphs in a compact and efficient way. They allow us to easily determine which vertices are adjacent to one another and can be used for a variety of graph algorithms and applications.

Here's the above explanation in markdown code:

An adjacency matrix is a square matrix that represents a graph. Each row and column of the matrix represents a vertex, and the values in the matrix indicate whether there is an edge between two vertices. If there is an edge between vertices i and j, then the (i, j) and (j, i) entries of the matrix are set to 1. If there is no edge between vertices i and j, then the (i, j) and (j, i) entries of the matrix are set to 0.

For example, consider the following graph:

A --- B
/ \ /
C---D---E---F


We can represent this graph using an adjacency matrix as follows:

A B C D E F
A 0 1 1 0 0 0
B 1 0 0 0 1 0
C 1 0 0 1 0 0
D 0 0 1 0 1 1
E 0 1 0 1 0 1
F 0 0 0 1 1 0


As you can see, the rows and columns of the matrix correspond to the vertices A through F, and the entries indicate whether there is an edge between each pair of vertices.

In some cases, we may also use a weighted adjacency matrix, where the entries represent the weight of the edge between two vertices instead of just 1 or 0.

To summarize, adjacency matrices are a useful tool for representing graphs in a compact and efficient way. They allow us to easily determine which vertices are adjacent to one another and can be used for a variety of graph algorithms and applications.
