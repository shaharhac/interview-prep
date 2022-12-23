# Graphs - WIP

A tree is actually a type of graph, but not all graphs are trees. Simply put, a tree is a connected graph without cycles.
A graph is simply a collection of nodes with edges between (some of) them.

Graphs can be either directed or undirected, while directed edges are like a one way street, endirected edges are like a two way street.

The Graph might consist of multiple isolated subgraphs. If there is a path between every pair of vertices, it is called a "connected graph".

The Graph can also have cycles. An "acyclic grpah" is one without cycles.

In terms of programming, there are two common ways to represent a graph:

* Adjacency List - Every node stores a list of adjacent nodes (in an undirected graph, an edge will be stored twice, once in a's list and once in b's list)

* Adjacency Matrices - An NxN matrix, where a true value at `matrix[i][j]` indicates an edge from node `i` to node `j`. (In an undirected graph, the matrix will be symmetric)

## Graph Search

There are two common ways to search a graph: deapth-first search (***DFS***) and breadth-first search (***BFS***)

### Depth-First Search

We start at the root (or any other node) and explore each branch completely before moving on to the next branch. That is, we go deep first (hence the name) before we go wide.

By itself the DFS isn't all that usful, but when augmented to perform other tasks such as count connected components, deterimne connectivity, or find bridges/articulation points, then DFS really shines.

***Time Complexity:*** `O(V + E)`

***Algorithm:***

1) Create a recursive function that takes the index of nmode and a visited array.
2) Mark the current node as visited and print the node.
3) Traverse all the adjacent and unmarked nodes and call the recursive function with index of adjacent node.

### Breadth-First Search

We start at the root (or any other node) and explore each neighbor before going on to any of their children. That is, we go wide first (hence the name) before we go deep.

BDS is often preferred if we want to find the shortest path (or a path) between two nodes.

***Algorithm:***

1) Visit the adjacent unvisited vertex. Mark it as visited. Insert it in a queue.
2) If no adjacent vertex is found, remove the first vertex from the queue.
3) Repeat Rule 1 and Rule 2 until the queue is empty.

### Bidirectional Search - WIP
