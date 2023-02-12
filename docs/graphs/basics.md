---
layout: default
title: Graph Basics
parent: Graphs
nav_order: 2

---

# Graphs

**Graph:** `G = (V, E)`, where for graph `G`, `V` is a set of vertices, and `E` is a set of edges. Every edge `E` is a tuple $`(v, w)`$ where $v, w \in V$

**Subgraph:** A subgraph `s` is a set of edges `e` and vertices `v` such that $e \in E$ and $v \in V$

## Graph ADT

The graph abstract data type (ADT) is defined as follows:

- `Graph()` creates a new, empty graph.
- `addVertex(vert)` adds an instance of `Vertex` to the graph.
- `addEdge(fromVert, toVert)` Adds a new, directed edge to the graph that connects two vertices.
- `addEdge(fromVert, toVert, weight)` Adds a new, weighted, directed edge to the graph that connects two vertices.
- `getVertex(vertKey)` finds the vertex in the graph named `vertKey`.
- `getVertices()` returns the list of all vertices in the graph.
- `in` returns `True` for a statement of the form `vertex in graph`, if the given vertex is in the graph, `False` otherwise.

### Representation 1: Adjacency Matrix

### Representation 2: Adjacency List

**Vertex** class:

- `addNeighbor(nbr,weight=0)`
- `getConnections()`
- `getId()`
- `getWeight(nbr)`

## Detecting Cycles in a Graph

{: .warning}

To_DO: Both for directed graphs and undirected graphs



# References

- [Runstone Academy PythonDS Book Chapter 8: Graphs](https://runestone.academy/ns/books/published/pythonds/Graphs/toctree.html)
- 