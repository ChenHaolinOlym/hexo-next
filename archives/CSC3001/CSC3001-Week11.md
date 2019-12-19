---
title: CSC3001 Week11
tags:
  - CSC3001
  - Discrete Mathematics
mathjax: true
categories:
  - note
  - CSC3001
date: 2019-11-30 09:54:01
---

Graph Coloring

## Graph Coloring

**Graph Coloring Problem:** Given a graph, color all the vertices so that adjacent vertices get different colors. 

**Objective:**  use minimum number of colors. 

**Defintion:** A graph is k-colorable if its vertices can be colored by k different colors so that adjacent vertices get different colors. 

### Optimal Coloring

**Definition:** min # colors for G is chromatic number, $\chi(G)$, $\chi(G) > 0$.

When there is no edges in a graph, the chromatic number is 1.

#### Simple Cycles

![image-20191204234818496](/image-20191204234818496.png)

$\chi(C_{even}) = 2$, $\chi(C_{odd}) = 3$

#### Complete Graphs

A graph is **complete** if there is an edge between every pair of distinct vertices.  We usually denote the complete graph of n vertices by $K^n$. $\chi(K_n) = n$

#### Wheels

With one vertex in the middle to connect every vertexes on the "edge" of the graph.

![image-20191204235147639](/image-20191204235147639.png)

$\chi(W_{odd}) = 4$, $\chi(W_{even}) = 3$

With one distinct color in the middle and 2/3 colors for even/odd cycles on the "edge".

#### Trees

**Claim:** $\chi$(a tree with two or more vertices) = 2.

**Proof:**

- Consider such a tree G and pick a vertex u as the “root”.
- The unique path between a vertex and u is of length either even or odd,
- it follows that all vertices will be colored by this process.
- So G is 2-colorable, and $\chi(G) \leq 2$.
- But adjacent vertices need to be colored differently, so $\chi(G) \geq 2$.
- Hence, $\chi(G) = 2$. 

#### Bipartite Graphs

**Fact:** A graph is 2-colorable if and only if it is bipartite. 

**Theorem:** A graph is bipartite if and only if it has no odd cycle. 

#### Estimate Chromatic Number

If there is a complete subgraph of size k, then we need at least k colors.

Let $\omega(G)$ be the largest size of a complete subgraph that G contains. $\chi(G) \geq \omega(G)$

But $\chi(G)$ could be arbitrarily large when $\omega(G)$ is relatively small, so $\omega(G)$ is not a good estimate for $\chi(G)$

## Applications

### Flight Gates

#### Conflict Graph

Each vertex represents a flight, and each edge represents a conflict.

![image-20191205133725352](/image-20191205133725352.png)

**Fact:** The flights can be scheduled using k gates iff this graph is k-colorable.

### Exam Scheduling

- Subjects conflict if student takes both, so they need different time slots. How short can the exam period be?
- This is a graph coloring problem. 
- Each course is a vertex, two courses are adjacent if there is a conflict. 
- The exams can be scheduled in k slots if and only if the graph is k-colorable. 

### Register Allocation

- Given a program, we want to execute it as quickly as possible.
- Calculations can be done most quickly if the values are stored in registers.
- But registers are very expensive, and there are only a few in a computer.
- Therefore, we need to use the registers effectively.
- This is a graph coloring problem
- To model this problem:
  - The live range of each variable is a vertex.
  - Add an edge when two live ranges overlap. 

### Summary

- To model a problem as a graph coloring problem, a standard recipe is to think of your resource (e.g. gates, time slots, registers) as colors, each object (e.g. flight, course, live range) as a vertex, and each edge as a conflict.
- Then, using fewest colors to color all the vertices is equivalent to using minimum amount of resource for all the objects so that there would be no conflicts. 

## Some Positive Results

### Maximum Degree

Suppose every vertex is of degree at most d, one can color it using at most d+1 colors. 

This is just a sufficient condition, we can generalize it to Maximum Degree Ordering.

### Maximum Degree Ordering

**Claim:** Suppose there is an ordering of the vertices $v_1 , \dots, v_n$ , such that each vertex has at most *d* ***fore neighbors***. Then the graph can be colored by **d+1** colors.

**fore neighbor:** If we put all the vertexes into a line, neighbors that is in the *left*/*right*(pre-determine) of that vertex is it's fore neighbor.

**Proof:** 

1. We color the vertices one by one following the ordering.
2. For each vertex $v_i$ , its fore neighbors are colored by at most *d* colors.
3. Hence we can color vi using the *d+1*-th color.
4. It follows that all vertices can be colored by *d+1* colors.  

**Construct such ordering:** Just pick any vertex of degree at most d, put it at the end and repeat. 

### Interval Graphs

Interval Graphs are conflict graphs of intervals.

For interval graphs,  minimum number of colors need = maximum size of a complete subgraph.

#### Theorem

For interval graph G, $\chi(G)$ = $\omega(G)$.

#### Proof

From the above we know that $\chi(G) \geq \omega(G)$, so we just need to prove that $\chi(G) \leq \omega(G)$.

**Lemma:** In an interval graph G, there is a vertex of degree at most $\omega(G) - 1$.

- Let $k = \omega(G)$. We will show that there is a vertex with degree k-1. Let v be the interval with leftmost right endpoint (earliest finishing time).  
- Any interval that intersects v must intersect v at the right endpoint.
- All the intervals that intersect v must intersect with each other, and thus they form a complete subgraph.
- Since $\omega(G) = k$, this complete subgraph is of size at most k, and thus v has at most k-1 neighbors. Therefore, v is a vertex of degree at most k-1. 

**Proof of the Theorem:** 

1. Pick the vertex v chosen in the Lemma.
2. Remove this vertex (and its incident edges) from the graph.
3. The resulting graph is also an interval graph, but smaller.
4. There is also a vertex of degree at most k-1 in this resulting graph.
5. Repeat 1-2 until the resulting graph becomes a single vertex.
6. So we have found an ordering of vertices with at most k-1 fore neighbors each. (exactly the same as before)
7. Therefore, the graph is k-colorable.  

## Planar Graphs

### Definition

**Map Coloring:** Color the map using minimum number of colors so that adjacent countries always have distinct colors. 

**Theorem:**  Every map is 4-colorable.

**Planar Graphs:** A graph is planar if there is a way to draw it in a plane without edges crossing. 

#### Euler's Formula

If a connected planar graph has *n* vertices, *m* edges, and *f* faces, then n – m + f = 2

#### Face

**Face:** A **face** of a *planar graph* is a region surrounded by a cycle such that the region doesn’t contain any vertices and edges. 

**Face Length:** The *face length* of a face is the number of edges in its face boundary 

**Bridge:** A single edge that connects two faces.

**Dongle:** A cycle but has vertexes inside.

## Euler's Formula

### Definition

If a connected planar graph has n vertices, m edges, and f faces, then n – m + f = 2

### Proof

Proof by induction on the number of vertices.

**Base Case:** (n = 1)

![image-20191207134452223](/image-20191207134452223.png)

f = m+1

**Inductive Step:** (n > 1)

![image-20191207134639283](/image-20191207134639283.png)

Number of faces is the same, although some faces get smaller.

By assumption, n’-m’+f’=2. This implies n-m+f=2.

### Further Questions

Is the number of faces always the same for different drawings of the same graph?

***YES***, because isomorphic graphs preserve (simple) cycles.

What if the graph is disconnected, say it has *k* connected components?

$n = \sum n_i , m = \sum m_i , f = \sum f_i - (k - 1) \Rightarrow n - m + f = k + 1$ 

## 6-coloring

### Theorem

Every planar graph is 6-colorable.

### Proof

#### Steps

1. Show that there are at most 3n-6 edges in a planar graph.
2. Show that there is a vertex of degree 5.
3. Show that there is a 6-coloring.  

#### Claim 1

**Claim:** If G is a simple planar graph with at least 3 vertices, then $m \leq 3n-6$

**Proof:** 

- Let $F_1, \dots, F_f$ be the face lengths.

- Note that $2m = \sum^f_{i=1}F_i$

- Since the graph is simple, $F_i \geq 3$ for each i.
- So $2m \geq 3f$
- Since m = n + f - 2
- $m \leq 3n -6$

#### Claim 2

**Claim:** Every simple planar graph has a vertex of degree at most 5. 

**Proof:** 

1. Suppose every vertex has degree at least 6.
2. By Handshaking Lemma, m ≥ 6n/2 = 3n, a contradiction.
3. So there exists a vertex v of degree at most 5. 

#### Claim 3

**Claim:** Every planar graph is 6-colorable. 

**Proof:** 

1. Proof by induction on the number of vertices.
2. Let v be a vertex of degree at most 5.
3. Remove v from the planar graph G.
4. Note that G-v is still a planar graph.
5. By assumption G-v is 6-colourable.
6. Since v has at most 5 neighbors,
7. we can always color v using the 6-th color. 







