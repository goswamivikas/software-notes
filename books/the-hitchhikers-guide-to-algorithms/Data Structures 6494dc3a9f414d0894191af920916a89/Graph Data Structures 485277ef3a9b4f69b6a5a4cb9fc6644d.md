# Graph Data Structures

**Input description:** A Graph $G$

**Problem description:** Represent graph G using a flexible, efficient data structure.

**Discussion:**

- two basic data structures for representing graphs are *adjacency matrices* and *adjacency lists*.
- *how big will your graph be? # of vertices and edges?* adjacency matrices make sense only for small or very dense graphs
- *how dense your graph be?* if very dense, adjacency matrices are better
- *which algorithm will you be implementing?* most DFS-based algorithms favor adjacency lists, while **certain algorithms like the all-pairs shortest path or involving queries like “$Is\;(i,j)\;in\;G$” favor adjacency matrices. If we are only querying then we can use the hash table of edges.
- *Will you modify the graph over the course of the computation?* efficient static graph implementations can be used when no edge insertion/deletions will be done following initial construction. attributes modification like weight, color etc are best handled as extra fields in the vertex or edge records of adjacency lists.
- *will your graph be a persistent online structure?* data structures and databases are two different things. graph databases like Neo4j are useful for representing networks in a persistent, online fashion
- *Planar Graphs* are those that can be drawn in the plane so no two edges cross.
- *Hypergraphs -* generalized graphs where each edge may link subsets of more than two vertices. [a two min explanation](https://www.youtube.com/watch?v=YGNaRFEa8PI).
- Two basic data structures for hypergraphs are:
    - *Incidence matrices,* which are analogous to adjacency matrices. the only difference would be that traditional graphs have exactly two non-zero entries in each column.
    - *Bipartite incidence structures,* are analogous to adjacency lists, and thus suited for sparse hypergraphs.
- effort should be made to make data structure as lean as possible, by packing your adjacency matrix in a bit vector or removing unnecessary pointers from your adjacency list representation.
- If your graph is extremely large, you may switch to hierarchical representation. two approaches exist to construct a hierarchical decomposition.
    - natural or application-specific way, for example, a network of roads and cities suggest a natural decomposition $-$ partition  the map into districts, towns, countries, and states
    - alternatively, you can run a graph partition algorithm

**Implementation Choices:**

- Adjacency Lists and Adjacency Matrices
- Suggested Implementation - [LEDA Graphs](http://www.algorithmic-solutions.info/leda_guide/graphs/graph.html)

**C++ Implementation:**

[The C++ Boost Graph Library](https://www.boost.org/doc/libs/1_78_0/libs/graph/doc/index.html)