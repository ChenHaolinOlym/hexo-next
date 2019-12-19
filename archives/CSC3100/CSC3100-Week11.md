---
title: CSC3100 Week11
tags:
  - CSC3100
  - Data Structure
  - Algorithm
mathjax: true
categories:
  - note
  - CSC3100
date: 2019-11-10 10:49:33
---

Graph Algorithms

## Concepts and Definitions

### Definition

- A graph G = (V, E) consists of a set of vertices, V, and a set of edges, E.
- Each edge (arc) is a pair (v, w), where v,w $\in$ V. An edge may have a weight (cost).
- If the pair is ordered, then the graph is directed graph.
- Vertex w is adjacent to v if and only if (v, w) $\in$ E.

### Application

Can be applicated in Maps, Schedules, Computer Networks, Htpertext and Circuits etc.

### Directed vs. Undirected

#### Directed Graph

- The *in-degree* of a vertex *v* is the number of edges (*u*, *v*) entering v.

- The *out-degree* of a vertex *v* is the number of edges (v, *u*) leaving v.

#### Undirected Graph

- The degree of a vertex v is the number of edges connecting v

### Graph and Path

- Complete graph
  - A graph with an edge between each pair of vertices

- Subgraph
  - A graph $(V’, E’)$ such that $V’ \subseteq V$ and $E’\subseteq E$

- Path from v to w
  - A sequence of vertices $<v_0, v_1, \dots, v_k>$ such that  $v_0=v$ and $v_k=w$

- Length of a path
  - Number of edges in the path

- w is reachable from v
  - If there is a path from v to w

- Simple path 
  - All the vertices in the path are distinct

### Cycles

- Cycles
  - A path $<v_0, v_1, \dots, v_k>$ forms a cycle if $v_0=v_k$ and $k\geq 2$

- Acyclic graph
  - A graph without any cycles

### Connected vs. Strongly Connected

- A graph is connected if there is a path from every vertex to every other vertex.

- A directed graph with this property is called strongly connected.
  - If a directed graph is not strongly connected, but the underlying graph (without direction to the edges) is connected, then the graph is said to be weakly connected.

- Examples of graph models include
  - Computer networks; 
  - Job scheduling

### Tree and Graph

- A tree is a connected, acyclic “undirected” graph

### Bipartite Graph

- A bipartite graph is an undirected graph G = (V, E) in which $V = V_1 + V_2$ and there are edges only between vertices in $V_1$ and $V_2$

## Graph Representation

### Adjacency Matrix Representation

#### Definition

- Assume vertices are numbered 1, 2, … , |V|

- The representation consists of a matrix $A_{|V|\times |V|}$:

- $$
  \begin{equation}
  a_{ij} = \left \{
  \begin{aligned}
  1 && \text{if (i, j)} \in E\\
  0 && \text{otherwise}
  \end{aligned}
  \right .
  \end{equation}
  $$

- ![image-20191206204420631](/image-20191206204420631.png)

- For undirected graphs, matrix A is symmetric:

  - $a_{ij} = a_{ji}$
  - $A = A^T$

#### Properties

- Memory required
  - $\Theta(V^2)$, independent on the number of edges in G

- Preferred when
  - The graph is **dense:** $|E|$ is close to $|V|^2$
  - We need to quickly determine if there is an edge between two vertices

- Time to determine if $(u, v) \in E$:
  - $\Theta(1)$

- Disadvantage
  - Waste space for spare graphs
  - No quick way to determine the vertices adjacent to another vertex.

- Time to list all vertices adjacent to u:
  - $\Theta(V)$

### Adjacency List Representation

#### Definition

- An array of |V| lists, one for each vertex in V

- Each list Adj[u] contains all the vertices v that are adjacent to u (i.e., there is an edge from u to v)

- Can be used for both directed and undirected graphs
- ![image-20191206211717560](/image-20191206211717560.png)

#### Properties

- Sum of “lengths” of all adjacency lists
  - Directed graph: |E|
    - edge (u, v) appears only once (i.e., in the list of **u**)
  - Undirected graph: 2|E|
    - edge (u, v) appears twice (i.e., in the lists of both **u** and **v**)

- Memory required
  - $\Theta(V + E)$

- Preferred when
  - The graph is **sparse**: $|E| \ll |V|^2$
  - We need to quickly determine the nodes adjacent to a given node.

- Disadvantage
  - No quick way to determine whether there is an edge between node u and v

- Time to determine if $(u, v) \in E$:
  - O(degree(u))

- Time to list all vertices adjacent to u:
  - $\Theta$(degree(u))​

### Representation in Weighted Graph

- Graphs for which each edge has an associated weight w(u, v)
  - w: *E* $\Rightarrow$ R, weight function

- Storing the weights of a graph
  - Adjacency list: 
    - Store w(u, v) along with vertex v in u’s adjacency list
  - Adjacency matrix:
    - Store w(u, v) at location (u, v) in the matrix
- ![image-20191206213132865](/image-20191206213132865.png)

## Topological Sort

- An ordering of all vertices in a directed acyclic graph, such that if there is a path from $v_i$ to $v_j$, then $v_j$ appears after $v_i$ in the ordering.

- If there is no path between $v_i$ and $v_j$, then any order between them is fine.

- Applications: job scheduling, logistics planning, course selection for each term

- Topological ordering is not possible if there is a cycle in the graph. 

- A DAG(Directed acyclic graph) has at least one topological ordering.

### Simple Algorithm

- Compute the indegree of all vertices from the adjacency information of the graph.
- Find any vertex with no incoming edges.
- Print this vertex, and remove it, and its edges.
- Apply this strategy to the rest of the graph.

### Improved Algorithm

- Keep all the unassigned vertices of indegree 0 in a queue.

- While queue not empty

- Remove a vertex in the queue.

- Decrement the indegree of all adjacent vertices.

- If the indegree of an adjacent vertex becomes 0, enqueue the vertex.

- Running time is O(|E|+|V|).
