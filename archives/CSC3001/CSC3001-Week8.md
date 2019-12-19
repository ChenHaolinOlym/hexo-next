---
title: CSC3001 Week8
tags:
  - CSC3001
  - Discrete Mathematics
categories:
  - note
  - CSC3001
date: 2019-11-10 10:50:38
---

Introduction to Graphs

## Graphs, Degrees

### Types of Graphs

#### Simple Graph

No multiedges, no loops, no directed edges:

![image-20191110160958413](/image-20191110160958413.png)

#### Directed Graph

![image-20191110161033856](/image-20191110161033856.png)

#### Multi-graph

![image-20191110161050054](/image-20191110161050054.png)

 Unless otherwise specified, all graphs in this course are simple.

### Simple Graph

A graph G=(V,E) consists of:

- A set of vertices, V
- A set of undirected edges, E
  - V(G) = {a,b,c,d,e,f}
  - E(G) = {ad,af,bd,be,cd,ce,df} 

![image-20191110161417797](/image-20191110161417797.png)

The vertices a,b are adjacent (neighbours) if the edge ab is present.

### Vertex Degrees

An edge uv is **<span style="color:red;">incident</span>** with the vertex *u* and the vertex *v*.

The **<span style="color:green;">neighbour set</span>** N(v) of a vertex v is the set of vertices adjacent to it. 

**<span style="color:blue;">degree of a vertex</span>** = the number of **<span style="color:red;">incident</span>** edges (loops counted twice.) 

The degree of a vertex v = the number of neighbours of v?

For multigraphs, **NO**. For simple graphs, **YES**.

### Handshaking Lemma

For any graph, sum of degrees = twice # edges 

**Lemma:** $2|E| = \sum_{v \in V} \text{deg}(v)$

**Corollary:** 

1. Sum of degree is an even number.
2. Number of odd degree vertices is even.

**Proof:** Each edge contributes 2 to the sum on the right. **Q.E.D.**

**Question:** Given a degree sequence, if the sum of degree is even, is it true that there is always a graph with such a degree sequence?

For simple graphs, **NO**, consider the degree sequence (3,1). For multigraphs (*with self loops*), **YES**! 

## Isomorphism

### Graph Isomorphism

All that matters is the *connections*.

Graphs with the same connections are ***isomorphic***.

Informally, two graphs are isomorphic if they are the same after *renaming*. 

Graph isomorphism has applications like fingerprint checking, molecules testing… 

**$G_1$ isomorphic to $G_2$ means there is a one-to-one mapping (*isomorphism*) of the vertices that is edge-preserving.**

$\exists \text{ one-to-one mapping }f: V_1 \rightarrow V_2 \text{ u—v } \in E_1 \text{ iff f(u)—f(v)} \in E_2$

If $G_1$ and $G_2$ are isomorphic, they have the same:

- Vertices
- Edges
- Degree sequence

### Checking Graph Isomorphism

To show two graphs are isomorphic, find a mapping and show that it is edge preserving.

To show two graphs are not isomorphic, find some isomorphic-preserving properties which is satisfied in one graph but not in the other.

## Path, Cycle, Connectedness

**Path:** Sequence of adjacent vertices.

**Simple Path:** All vertices different.

### Connectedness

- Vertices *v*, *w* are *connected* if and only if there is a path starting at *v* and ending at *w*.
- A graph is *connected* iff every pair of vertices are connected. 

 Every graph consists of disjoint connected pieces (called **connected components**) 

 So a graph is connected if and only if it has only 1 connected component.

### Simple Cycles

A (simple) *cycle* is a connected graph whose vertices are all of **degree 2**. In particular, for multigraphs, a loop is a cycle.

### Shortest Paths

A path between u and v is *shortest* if it uses the minimum number of edges among all u-v paths. 

## Tree

**Forest:** Graphs with no cycles

**Tree:** Connected graphs with no cycles

**Leaf:** a vertex of degree 1

### Tree Characterization

**Definition:** A tree is a connected graph with no cycles.

**Claim:** 

- In a tree, there is a unique simple path between every pair of vertices.

- A tree cannot have no leaves
- A tree which have *n* vertices have *m=n-1* edges

#### Characterization by Paths:

A graph is a tree if and only if there is a unique simple path between every pair of vertices.

#### Characterization by Number of Edges:

A graph is a tree if and only if it is connected and has n-1 edges.

## Eulerian Cycle

### Euler's Theorem

- A graph has an Eulerian path if and only if it is connected and has at most two vertices with an odd number of edges.
- A connected graph has an Eulerian path if and only if it has zero or two vertices with odd degrees.
- A connected graph has an Eulerian cycle if and only if every vertex is of even degree.
- All of the above are equal

The technique can be easily generalized to multigraphs, but we only talk about simple graphs.

#### Eulerian Cycle

a cycle that visits each edge exactly once.

**Claim 1:** If the edges of  a connected graph can be partitioned into simple cycles, then we can construct an Eulerian cycle.

**Claim 2:** If every vertex is of even degree, the edges can be partitioned into simple cycles.

**Proof:**

- Let C be a simple cycle.
- Remove the edges in C from the graph G and call the new graph G’.
- So the degree of each vertex is either unchanged or decreased by two.
- So every vertex of the graph G’ is still of even degree.
- Note that G’ has fewer edges than G.
- In finite steps, G’ can be partitioned into simple cycles $C_1$ , $C_2$ , …, $C_k$.
- So the original graph G can be partitioned into simple cycles $C_1$ , $C_2$ , …, $C_k$.

With **Claim 1** and **Claim 2**, Euler's Theorem can be proved.

#### Odd-Degree Case in Eulerian

**Claim 3:**  If a connected graph has two vertices of odd degree, then it has an Eulerian path.

It can be easily proved.

Till now we are done.

## Directed Graphs

A digraph G=(V,A) consists of: a set of vertices, *V* a set of directed **edges** (**arcs**), *A*

![image-20191112163503036](/image-20191112163503036.png)

- V(G) = {a,b,c,d,e,f}
- A(G) = {da, fa, db, eb, dc, ec, fd} 

For an arc *uv*, we say *u* is the **tail** of the arc and *v* is the **head** of the arc. Also, we say *v* is an **out-neighbor** of *u*, and *u* is an **in-neighbor** of *v*. 

![image-20191112162509934](/image-20191112162509934.png)

### In-Degrees and Out-Degrees

The **out-degree** of a vertex *v* is the number of **out-neighbors** of *v*; similarly, the **in-degree** of a vertex *v* is the number of **in-neighbors** of *v*.

### Directed Paths

Informally, a directed path is a path that follows the arcs.

**Directed Path:** sequence of vertices $v_1$ , $v_2$ , …, $v_k$ such that there is an arc from $v_i$ to $v_{i+1}$ for each i = 1, …, k-1. 

**Simple Directed Path:** a directed path with no repeated vertices.

### Directed Cycles

A digraph is *connected* if replacing its arcs by undirected edges results in a connected simple graph.  

A **directed cycle** is a connected digraph that the *out-degree* and *indegree* are both 1 for every vertex.  