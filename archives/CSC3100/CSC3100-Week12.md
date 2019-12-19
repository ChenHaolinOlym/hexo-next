---
title: CSC3100 Week12
tags:
  - CSC3100
  - Data Structure
  - Algorithm
mathjax: true
categories:
  - note
  - CSC3100
date: 2019-11-10 10:50:27
---

Shortest Path

## Shortest Path

### Problems

- How can we find the shortest route between two points on a road map?

- Model the problem as a graph problem:
  - Road map is a weighted graph: 
    - vertices = cities
    - edges = road segments between cities
    - edge weights = road distances
  - Goal: find a shortest path between two vertices (cities)

- Input

  - Directed Graph G = (V, E)
  - Weight Function w: $E\rightarrow R$

- Weight of the Path $p = <v_0, v_1, \dots, v_k>$

  - $w(p) = \sum^k_{i=1}w(v_{i-1}, v_{i})$

- Shortest-path Weight from u to v:

  - $$
    \begin{equation}
    \delta(u,v) = \min \left \{
    \begin{aligned}
    w(p) && \text{if there exists a path from u to v} \\
    \infty && \text{otherwise}
    \end{aligned}
    \right .
    \end{equation}
    $$

- **Note:** there might be _**multiple** shortest paths_ from u to v.

### Variants

- **Single-source shortest paths**
  - G = (V, E) $\Rightarrow$ find a shortest path from a given source vertex s to each vertex $v \in V$

- **Single-destination shortest paths**
  - Find a shortest path to a given destination vertex t from each vertex v
  - Reversing the direction of each edge $\Rightarrow$ single-source

- **Single-pair shortest path**
  - Find a shortest path from u to v for given vertices u and v

- **All-pairs shortest-paths**
  - Find a shortest path from u to v for every pair of vertices u and v

### Negative-Weight Edges

- Negative-weight edges may form negative-weight cycles

- If such cycles are reachable from the source, then $\delta(s, v)$ is not properly defined!
  - Keep going around the cycle, and get $w(s, v) = - \infty$ for all v on the cycle

#### Cycles

Shortest weight cannot contain cycles:

- Negative-weight cycles:
  - Shortest path is not well defined
- Positive-weight cycles:
  - By removing the cycle, we can get a shorter path 

### Optimal Substructure Theorem







### Algorithm



