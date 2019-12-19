---
title: CSC3100 Week13
tags:
  - CSC3100
  - Algorithm
  - Data Structure
mathjax: true
categories:
  - note
  - CSC3100
date: 2019-11-29 21:04:26
---

Minimum Spanning Tree

## Definitions

- Spanning Tree
  - A tree (i.e., connected, acyclic graph) which contains all the vertices of the graph

- Minimum Spanning Tree
  - Spanning tree with the **minimum sum of weights**
- ![image-20191207203101130](/image-20191207203101130.png)
  
- Spanning forest
  - If a graph is not connected, then there is a spanning tree for each connected component of the graph

## Applications

- Find the least expensive way to connect a set of cities, terminals, computers, etc.

## Properties

- Minimum spanning tree is **not** unique

- MST has no cycles – see why:
  - We can take out an edge of a cycle, and still have the vertices connected while reducing the cost

- \# of edges in a MST:
  - |V| - 1 

