---
title: CSC3100 Week5
tags:
  - CSC3100
  - Data Structure
  - Algorithm
categories:
  - note
  - CSC3100
date: 2019-09-26 16:00:36
mathjax: true
---

Priority Queue and Heap

## Motivation

For a simple FIFO Queue, sometimes the queue will be jammed by a huge job while waiting for just one printout.

There's three important point:

- Short job may go first
- Most urgent cases should go first
- Tasks with highest priority should go first

## Priority Queue ADT(Abstract Data Type)

In Priority Queue, every element comes along with a priority number.

### Priority Queue Operations

- insert, deletemin, create, isempty

### Priority Queue Property

For two elements in the queue, *x* and *y*, if *x* has a **_lower priority_** value than *y*, *x* will be deleted before *y*.

### Priority Queue Implementation

#### Simple Linked List

- Insert at the front in O(1)
- Delete minimum in O(N)

#### Sorted Linked List

- Insert in O(N)
- Delete minimum in O(1)

#### Sorted Array

- Insert in O(N)
- Delete minimum in O(N)

#### Binary Heap

- Insert in O(logN)
- Delete minimum in O(N)

##### Property of Binary Heap

- Struture Property
- Heap Order Property

#### Binary Search Tree(To be explained later)

- Insert in O(logN)
- Delete minimum in O(logN)

## Binary Heap

### Structured Property

- A heap is a binary tree that is completely filled except at the bottom level, which is filled from the left to right
- A complete binary tree of height *h* has between $2^h$ and $2^h -1$ nodes
- The height of a complete binary tree = $\lfloor$ $log N \rfloor$ (round down, e.g. $\lfloor 2.7 \rfloor$  = 2).
- The height of a tree which have only one node is 0.

A complete binary tree can be represented in an array without using pointers. (How to implement the array back to heap has an order)

For a node at *i* in the array, it's children is *2i* and *2i+1*, it's parent is at $\lfloor \frac{i}{2} \rfloor$

### Ordered Property

The value at any node should be smaller than(or equal to) any of its decendents. So the node with minimum value is at the root.

### Functions

- Insert
- DeleteMin
- DecreaseKey
- buildHeap

#### insert

1. Create a hole
2. Percolate the hole up

Percolate up: If the velue you want to insert is smaller than the hole's parent, switch the hole with its parent.

#### deleteMin

The element at the root is the minimum and is to removed. Remove it and a hole is created, fill the hole with the last node X, and percolate it down.

Percolate down: If the value in the hole is bigger than its decendents, switch the hole with its **smaller** decendent.

**Attention:** Some node may have only one child, so be careful when coding.

#### decreaseKey

##### Definition

*decreaseKey(P, $\Delta$)* Lower the key value at position P by $\Delta$

Fix the heap order by percolating up

##### Application

Advance the priority of a paticular job.

#### buildHeap

N successive appends at the end of the array, each takes O(1). The tree is unordered.

Then percolate down until it's ordered.

##### Complexity Analize

At most $\frac{n}{4}$ percolate down 1 level
At most $\frac{n}{8}$ percolate down 2 level
...

$1\frac{n}{4}+2\frac{n}{8}+3\frac{n}{16}+... = \sum_{i=1}^{logn}i\frac{n}{2^{i+1}} = n$

## d-heap

### Definition

d-heap is exactly like a binary heap except that all nodes have d children (A binary heap is also called 2-heap)

### Remark

- Insert operation: $O(log_dN)$;
- DeleteMin operation: $O(dlog_dN)$;
- Useful in some applications where #INSERT >= #DeleteMin
- In practice, 4-heap outperforms 2-heap.

## Load Balancing

Assign jobs to servers basing on the loading of the servers

Use heap to assign servers.
